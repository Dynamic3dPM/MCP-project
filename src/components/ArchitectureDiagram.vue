<template>
  <div class="architecture-diagram">
    <svg width="100%" height="450" viewBox="0 0 600 450" xmlns="http://www.w3.org/2000/svg">
      <!-- Gradient Definitions -->
      <defs>
        <linearGradient id="layerGradient" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#e3f2fd;stop-opacity:1" />
          <stop offset="100%" style="stop-color:#bbdefb;stop-opacity:1" />
        </linearGradient>
        <linearGradient id="aiGradient" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#1976d2;stop-opacity:1" />
          <stop offset="100%" style="stop-color:#1565c0;stop-opacity:1" />
        </linearGradient>
        <filter id="shadow" x="-50%" y="-50%" width="200%" height="200%">
          <feDropShadow dx="2" dy="4" stdDeviation="3" flood-color="rgba(0,0,0,0.3)"/>
        </filter>
        <marker id="arrowhead" markerWidth="12" markerHeight="10" 
                refX="10" refY="5" orient="auto" fill="#1976d2">
          <polygon points="0 0, 12 5, 0 10" />
        </marker>
      </defs>

      <!-- Background Pattern -->
      <pattern id="gridPattern" width="20" height="20" patternUnits="userSpaceOnUse">
        <path d="M 20 0 L 0 0 0 20" fill="none" stroke="#f0f0f0" stroke-width="1" opacity="0.3"/>
      </pattern>
      <rect width="100%" height="100%" fill="url(#gridPattern)" />

      <!-- Resource Layer -->
      <g class="layer-group" style="animation-delay: 0.2s">
        <rect x="50" y="50" width="500" height="80" 
              fill="url(#layerGradient)" 
              stroke="#1976d2" 
              stroke-width="2" 
              rx="8" 
              filter="url(#shadow)"
              class="layer-rect layer-1" />
        <circle cx="100" cy="90" r="15" fill="#4fc3f7" class="layer-icon">
          <animate attributeName="r" values="15;18;15" dur="2s" repeatCount="indefinite"/>
        </circle>
        <text x="130" y="85" font-size="18" fill="#1976d2" font-weight="bold" class="layer-title">Resource Layer</text>
        <text x="130" y="105" font-size="13" fill="#666" class="layer-subtitle">External Resources & Data Sources</text>
        
        <!-- Resource Icons -->
        <g class="resource-icons">
          <circle cx="400" cy="75" r="8" fill="#4caf50" class="resource-dot">
            <animate attributeName="opacity" values="0.5;1;0.5" dur="1.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="430" cy="85" r="8" fill="#ff9800" class="resource-dot">
            <animate attributeName="opacity" values="0.5;1;0.5" dur="1.5s" begin="0.3s" repeatCount="indefinite"/>
          </circle>
          <circle cx="460" cy="75" r="8" fill="#9c27b0" class="resource-dot">
            <animate attributeName="opacity" values="0.5;1;0.5" dur="1.5s" begin="0.6s" repeatCount="indefinite"/>
          </circle>
        </g>
      </g>

      <!-- Tool Layer -->
      <g class="layer-group" style="animation-delay: 0.4s">
        <rect x="50" y="150" width="500" height="80" 
              fill="url(#layerGradient)" 
              stroke="#1976d2" 
              stroke-width="2" 
              rx="8" 
              filter="url(#shadow)"
              class="layer-rect layer-2" />
        <circle cx="100" cy="190" r="15" fill="#ff9800" class="layer-icon">
          <animate attributeName="r" values="15;18;15" dur="2s" begin="0.5s" repeatCount="indefinite"/>
        </circle>
        <text x="130" y="185" font-size="18" fill="#1976d2" font-weight="bold" class="layer-title">Tool Layer</text>
        <text x="130" y="205" font-size="13" fill="#666" class="layer-subtitle">Tool Integration & Execution</text>
        
        <!-- Tool Icons -->
        <g class="tool-icons">
          <rect x="380" y="170" width="20" height="20" fill="#2196f3" rx="3" class="tool-box">
            <animateTransform attributeName="transform" type="rotate" values="0 390 180;360 390 180" dur="4s" repeatCount="indefinite"/>
          </rect>
          <rect x="410" y="175" width="15" height="15" fill="#4caf50" rx="2" class="tool-box">
            <animateTransform attributeName="transform" type="rotate" values="0 417.5 182.5;360 417.5 182.5" dur="3s" repeatCount="indefinite"/>
          </rect>
          <rect x="435" y="170" width="18" height="18" fill="#e91e63" rx="3" class="tool-box">
            <animateTransform attributeName="transform" type="rotate" values="0 444 179;360 444 179" dur="5s" repeatCount="indefinite"/>
          </rect>
        </g>
      </g>

      <!-- Protocol Layer -->
      <g class="layer-group" style="animation-delay: 0.6s">
        <rect x="50" y="250" width="500" height="80" 
              fill="url(#layerGradient)" 
              stroke="#1976d2" 
              stroke-width="2" 
              rx="8" 
              filter="url(#shadow)"
              class="layer-rect layer-3" />
        <circle cx="100" cy="290" r="15" fill="#9c27b0" class="layer-icon">
          <animate attributeName="r" values="15;18;15" dur="2s" begin="1s" repeatCount="indefinite"/>
        </circle>
        <text x="130" y="285" font-size="18" fill="#1976d2" font-weight="bold" class="layer-title">Protocol Layer</text>
        <text x="130" y="305" font-size="13" fill="#666" class="layer-subtitle">Standardized Communication</text>
        
        <!-- Protocol Wave Animation -->
        <g class="protocol-waves">
          <path d="M 380 280 Q 400 270 420 280 Q 440 290 460 280" stroke="#9c27b0" stroke-width="2" fill="none" class="wave">
            <animate attributeName="opacity" values="0;1;0" dur="2s" repeatCount="indefinite"/>
          </path>
          <path d="M 385 290 Q 405 280 425 290 Q 445 300 465 290" stroke="#9c27b0" stroke-width="2" fill="none" class="wave">
            <animate attributeName="opacity" values="0;1;0" dur="2s" begin="0.5s" repeatCount="indefinite"/>
          </path>
          <path d="M 390 300 Q 410 290 430 300 Q 450 310 470 300" stroke="#9c27b0" stroke-width="2" fill="none" class="wave">
            <animate attributeName="opacity" values="0;1;0" dur="2s" begin="1s" repeatCount="indefinite"/>
          </path>
        </g>
      </g>

      <!-- AI System -->
      <g class="ai-system" style="animation-delay: 0.8s">
        <rect x="50" y="350" width="500" height="60" 
              fill="url(#aiGradient)" 
              stroke="#1976d2" 
              stroke-width="3" 
              rx="12" 
              filter="url(#shadow)"
              class="ai-rect" />
        
        <!-- AI Brain Icon -->
        <g class="ai-brain">
          <circle cx="100" cy="380" r="20" fill="#ffffff" opacity="0.9">
            <animate attributeName="r" values="20;23;20" dur="1.5s" repeatCount="indefinite"/>
          </circle>
          <path d="M 90 375 Q 100 365 110 375 Q 105 385 100 380 Q 95 385 90 375" fill="#1976d2" class="brain-shape">
            <animateTransform attributeName="transform" type="scale" values="1;1.1;1" dur="1.5s" repeatCount="indefinite"/>
          </path>
        </g>
        
        <text x="140" y="385" font-size="20" fill="white" font-weight="bold" class="ai-title">AI System</text>
        
        <!-- Neural Network Animation -->
        <g class="neural-network">
          <circle cx="400" cy="370" r="4" fill="white" class="neuron">
            <animate attributeName="r" values="4;6;4" dur="1s" repeatCount="indefinite"/>
          </circle>
          <circle cx="430" cy="375" r="4" fill="white" class="neuron">
            <animate attributeName="r" values="4;6;4" dur="1s" begin="0.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="460" cy="370" r="4" fill="white" class="neuron">
            <animate attributeName="r" values="4;6;4" dur="1s" begin="0.4s" repeatCount="indefinite"/>
          </circle>
          <circle cx="415" cy="390" r="4" fill="white" class="neuron">
            <animate attributeName="r" values="4;6;4" dur="1s" begin="0.6s" repeatCount="indefinite"/>
          </circle>
          <circle cx="445" cy="390" r="4" fill="white" class="neuron">
            <animate attributeName="r" values="4;6;4" dur="1s" begin="0.8s" repeatCount="indefinite"/>
          </circle>
          
          <!-- Neural Connections -->
          <line x1="400" y1="370" x2="430" y2="375" stroke="white" stroke-width="1" opacity="0.6" class="connection">
            <animate attributeName="opacity" values="0.3;0.8;0.3" dur="2s" repeatCount="indefinite"/>
          </line>
          <line x1="430" y1="375" x2="460" y2="370" stroke="white" stroke-width="1" opacity="0.6" class="connection">
            <animate attributeName="opacity" values="0.3;0.8;0.3" dur="2s" begin="0.3s" repeatCount="indefinite"/>
          </line>
          <line x1="400" y1="370" x2="415" y2="390" stroke="white" stroke-width="1" opacity="0.6" class="connection">
            <animate attributeName="opacity" values="0.3;0.8;0.3" dur="2s" begin="0.6s" repeatCount="indefinite"/>
          </line>
          <line x1="430" y1="375" x2="445" y2="390" stroke="white" stroke-width="1" opacity="0.6" class="connection">
            <animate attributeName="opacity" values="0.3;0.8;0.3" dur="2s" begin="0.9s" repeatCount="indefinite"/>
          </line>
        </g>
      </g>

      <!-- Animated Arrows with Data Flow -->
      <g class="data-flow">
        <line x1="300" y1="130" x2="300" y2="150" stroke="#1976d2" stroke-width="3" marker-end="url(#arrowhead)" class="flow-arrow">
          <animate attributeName="stroke-dasharray" values="0,20;20,0" dur="1.5s" repeatCount="indefinite"/>
        </line>
        <circle cx="305" cy="140" r="3" fill="#4fc3f7" class="data-packet">
          <animateMotion dur="1.5s" repeatCount="indefinite">
            <mpath href="#path1"/>
          </animateMotion>
        </circle>
        
        <line x1="300" y1="230" x2="300" y2="250" stroke="#1976d2" stroke-width="3" marker-end="url(#arrowhead)" class="flow-arrow">
          <animate attributeName="stroke-dasharray" values="0,20;20,0" dur="1.5s" begin="0.5s" repeatCount="indefinite"/>
        </line>
        <circle cx="305" cy="240" r="3" fill="#ff9800" class="data-packet">
          <animateMotion dur="1.5s" begin="0.5s" repeatCount="indefinite">
            <mpath href="#path2"/>
          </animateMotion>
        </circle>
        
        <line x1="300" y1="330" x2="300" y2="350" stroke="#1976d2" stroke-width="3" marker-end="url(#arrowhead)" class="flow-arrow">
          <animate attributeName="stroke-dasharray" values="0,20;20,0" dur="1.5s" begin="1s" repeatCount="indefinite"/>
        </line>
        <circle cx="305" cy="340" r="3" fill="#9c27b0" class="data-packet">
          <animateMotion dur="1.5s" begin="1s" repeatCount="indefinite">
            <mpath href="#path3"/>
          </animateMotion>
        </circle>
      </g>

      <!-- Hidden paths for data packet animation -->
      <defs>
        <path id="path1" d="M 300 130 L 300 150" />
        <path id="path2" d="M 300 230 L 300 250" />
        <path id="path3" d="M 300 330 L 300 350" />
      </defs>

      <!-- Side Labels -->
      <g class="side-labels">
        <text x="20" y="95" font-size="12" fill="#666" writing-mode="tb">Data</text>
        <text x="20" y="195" font-size="12" fill="#666" writing-mode="tb">Tools</text>
        <text x="20" y="295" font-size="12" fill="#666" writing-mode="tb">Protocol</text>
        <text x="20" y="385" font-size="12" fill="#666" writing-mode="tb">AI</text>
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'ArchitectureDiagram',
  mounted() {
    this.animateOnVisible()
  },
  methods: {
    animateOnVisible() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const svg = entry.target.querySelector('svg')
            if (svg) {
              svg.classList.add('visible')
            }
          }
        })
      }, { threshold: 0.3 })

      observer.observe(this.$el)
    }
  }
}
</script>

<style scoped>
.architecture-diagram {
  max-width: 100%;
  overflow-x: auto;
  padding: 20px;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  border-radius: 12px;
  box-shadow: inset 0 2px 10px rgba(0,0,0,0.1);
}

.architecture-diagram svg {
  min-width: 600px;
  filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
}

/* Layer Animations */
.layer-group {
  animation: slideInFromLeft 0.8s ease-out forwards;
  opacity: 0;
  transform: translateX(-50px);
}

.layer-rect {
  transition: all 0.3s ease;
}

.layer-rect:hover {
  stroke-width: 3;
  filter: url(#shadow) brightness(1.05);
}

.layer-1:hover { stroke: #4fc3f7; }
.layer-2:hover { stroke: #ff9800; }
.layer-3:hover { stroke: #9c27b0; }

/* AI System Animation */
.ai-system {
  animation: slideInFromBottom 1s ease-out forwards;
  opacity: 0;
  transform: translateY(30px);
}

.ai-rect {
  transition: all 0.3s ease;
}

.ai-rect:hover {
  stroke-width: 4;
  filter: url(#shadow) brightness(1.1);
}

/* Icon Animations */
.layer-icon {
  cursor: pointer;
  transition: all 0.3s ease;
}

.layer-icon:hover {
  transform: scale(1.2);
}

.resource-dot {
  cursor: pointer;
  transition: all 0.3s ease;
}

.resource-dot:hover {
  transform: scale(1.5);
}

.tool-box {
  cursor: pointer;
  transition: all 0.3s ease;
}

.tool-box:hover {
  transform: scale(1.2);
}

.neuron {
  cursor: pointer;
  transition: all 0.3s ease;
}

.neuron:hover {
  transform: scale(1.5);
}

/* Flow Animations */
.flow-arrow {
  stroke-dasharray: 5,5;
  animation: dash 2s linear infinite;
}

.data-packet {
  filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
}

/* Text Animations */
.layer-title, .ai-title {
  transition: all 0.3s ease;
}

.layer-title:hover, .ai-title:hover {
  transform: scale(1.05);
}

/* Visibility Animation */
svg.visible .layer-group {
  animation-play-state: running;
}

svg.visible .ai-system {
  animation-play-state: running;
}

/* Keyframes */
@keyframes slideInFromLeft {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInFromBottom {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes dash {
  to {
    stroke-dashoffset: -20;
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .architecture-diagram {
    padding: 10px;
  }
  
  .architecture-diagram svg {
    min-width: 500px;
    height: 350px;
  }
  
  .layer-title, .ai-title {
    font-size: 14px;
  }
  
  .layer-subtitle {
    font-size: 11px;
  }
}

@media (max-width: 480px) {
  .architecture-diagram svg {
    min-width: 400px;
    height: 300px;
  }
  
  .layer-title, .ai-title {
    font-size: 12px;
  }
  
  .layer-subtitle {
    font-size: 10px;
  }
}
</style>