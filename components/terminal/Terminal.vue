<template>
  <div class="terminal-container">
    <div class="terminal-header">
      <span>~ Terminal</span>
    </div>
    <div class="terminal-body">
      <div class="terminal-output" v-for="(output, index) in outputs" :key="index">
        <pre>{{ output }}</pre>
      </div>
      <div class="terminal-input-line">
        <span>jenny@jenos: $</span>
        <input
          type="text"
          class="terminal-input"
          v-model="command"
          @keyup.enter="executeCommand"
          placeholder="Type a command..."
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      command: "",
      outputs: [
        "Welcome to your Portfolio Terminal! Type 'help' to see the list of available commands.",
      ],
    };
  },
  methods: {
    executeCommand() {
      this.outputs.push(`jenny@jenos: $ ${this.command}`);
      const command = this.command.trim().toLowerCase();

      if (command === "help") {
        this.outputs.push(
          "Available commands:\n- date\n- about\n- skills\n- experience\n- resume\n- education\n- github\n- linkedin\n- clear"
        );
      } else if (command === "clear") {
        this.outputs = [];
      } else if (command === "date") {
        const currentDate = new Date().toString();
        this.outputs.push(currentDate);
      } else if (command === "about") {
        this.outputs.push(
          "Software Engineer with experience in developing and integrating full-stack web applications\n using Java, JavaScript, HTML, CSS, React.js, Node.js.\n\n" +
          "Skilled in TensorFlow, Python, data processing, and deploying optimized software systems.\n" +
          "Passionate about AI, machine learning, and full-stack programming."
        );
      } else if (command === "skills") {
        this.outputs.push(
          "Programming Languages: JavaScript, TypeScript, Python, Java, C, C#, C++, SQL\n" +
          "Front-end: HTML5, CSS3, React.js, Next.js, Node.js, Styled Components, Tailwind CSS\n" +
          "Mobile: React Native, Swift, Kotlin\n" +
          "Testing: Cypress, Jest, React Testing Library\n" +
          "Design: Adobe Photoshop, Adobe XD, Figma, Sketch\n" +
          "Version Control and Tools: Git, VSCode, WebStorm, Jira, Figma\n" +
          "Methodologies: Agile/Scrum, Kanban"
        );
      } else if (command === "experience") {
        this.outputs.push(
          "ClearSet.AI (Jan 2024 - Present):\n" +
          "  - Designed and developed user interfaces and full-stack applications.\n" +
          "  - Integrated front-end components with APIs and back-end services.\n" +
          "  - Used TensorFlow and Python for data processing and ML integration.\n" +
          "  - Contributed to the implementation of AI-driven services using python and google collab.\n\n" +
          "Vumi Group (Jan 2024 - Jul 2024):\n" +
          "  - Developed, maintained and deployed software using XML, SQL, Django, React, Java, AWS.\n" +
          "  - tested software and ensured that it was ready for deployment and release.\n" +
          "  - contributed to the implementation of new features and bug fixes that to improved\n" + "  the overall onboarding experience.\n\n" +
          "Best Buy (Jan 2020 - Jan 2023):\n" +
          "  - Provided technical advice and recommended computer configurations based on customer's needs.\n" +
          "  - contributed to tech support and user experiences that resulted in customer retention ." 
        );
      } else if (command === "resume") {
        window.open(
          "https://drive.google.com/file/d/1ZPHoTWTOCn6mn-JuOU-Qtq-VJULL5zCA/view?usp=drive_link",
          "_blank"
        );
        this.outputs.push("Opening resume...");
      } else if (command === "education") {
        this.outputs.push(
          "B.S. in Computer Engineering:\nFlorida International University, Miami, Florida"
        );
      } else if (command === "github") {
        window.open(
          "https://github.com/jeniferp0122?tab=repositories",
          "_blank"
        );
        this.outputs.push("Opening GitHub profile...");
      } else if (command === "linkedin") {
        window.open(
          "https://www.linkedin.com/in/jennifer-pantoja-a318561b8",
          "_blank"
        );
        this.outputs.push("Opening LinkedIn profile...");
      } else {
        this.outputs.push(`Command '${this.command}' not found.`);
      }

      this.command = "";
      this.scrollToBottom();
    },
    scrollToBottom() {
      this.$nextTick(() => {
        const terminalBody = this.$el.querySelector(".terminal-body");
        terminalBody.scrollTop = terminalBody.scrollHeight;
      });
    },
  },
};
</script>

<style scoped>
.terminal-container {
  width: 100%;
  max-width: none;
  background-color: #1e1e1e;
  color: #00ff00;
  border: 1px solid #008000;
  border-radius: 5px;
  font-family: 'Courier New', Courier, monospace;
  margin: 0 auto;
  height: 750px;
}

.terminal-header {
  background-color: rgba(3, 37, 3, 0.9);
  color: #00ff00;
  font-weight: bold;
  padding: 10px;
  border-radius: 5px 5px 0 0;
  text-align: left;
}

.terminal-body {
  padding: 10px;
  height: calc(100% - 60px);
  overflow-y: auto;
  background-color: #000;
  width: 100%;
}

.terminal-output {
  margin: 6px 0;
  font-size: 0.9rem;
  white-space: pre-wrap;
}

.terminal-input-line {
  display: flex;
  align-items: center;
  margin-top: 10px;
  background-color: transparent;
  border: none;
  box-shadow: none;
}

.terminal-input-line span {
  margin-right: 10px;
  white-space: nowrap;
  display: inline-block;
  vertical-align: middle;
}

.terminal-input {
  background: none;
  border: none;
  box-shadow: none;
  outline: none;
  color: #00ff00;
  font-family: inherit;
  font-size: 1rem;
  flex-grow: 1;
  padding: 0;
}

.terminal-input::placeholder {
  color: #00ff00;
  opacity: 0.7;
}

.terminal-input-line input[type="text"] {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}
</style>




