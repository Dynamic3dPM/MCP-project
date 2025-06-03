<template>
  <div class="architecture-diagram">
    <svg width="100%" height="400" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
      <!-- Resource Layer -->
      <rect x="50" y="50" width="500" height="80" fill="#f5f5f5" stroke="#1976d2" stroke-width="2"/>
      <text x="300" y="90" text-anchor="middle" font-size="16" fill="#1976d2" font-weight="bold">Resource Layer</text>
      <text x="300" y="120" text-anchor="middle" font-size="12" fill="#666">External Resources & Data Sources</text>

      <!-- Tool Layer -->
      <rect x="50" y="150" width="500" height="80" fill="#f5f5f5" stroke="#1976d2" stroke-width="2"/>
      <text x="300" y="190" text-anchor="middle" font-size="16" fill="#1976d2" font-weight="bold">Tool Layer</text>
      <text x="300" y="220" text-anchor="middle" font-size="12" fill="#666">Tool Integration & Execution</text>

      <!-- Protocol Layer -->
      <rect x="50" y="250" width="500" height="80" fill="#f5f5f5" stroke="#1976d2" stroke-width="2"/>
      <text x="300" y="290" text-anchor="middle" font-size="16" fill="#1976d2" font-weight="bold">Protocol Layer</text>
      <text x="300" y="320" text-anchor="middle" font-size="12" fill="#666">Standardized Communication</text>

      <!-- AI System -->
      <rect x="50" y="350" width="500" height="40" fill="#1976d2" stroke="#1976d2" stroke-width="2"/>
      <text x="300" y="375" text-anchor="middle" font-size="16" fill="white" font-weight="bold">AI System</text>

      <!-- Arrows -->
      <defs>
        <marker id="arrowhead" markerWidth="10" markerHeight="7" 
                refX="9" refY="3.5" orient="auto">
          <polygon points="0 0, 10 3.5, 0 7" fill="#1976d2" />
        </marker>
      </defs>
      
      <line x1="300" y1="130" x2="300" y2="150" stroke="#1976d2" stroke-width="2" marker-end="url(#arrowhead)"/>
      <line x1="300" y1="230" x2="300" y2="250" stroke="#1976d2" stroke-width="2" marker-end="url(#arrowhead)"/>
      <line x1="300" y1="330" x2="300" y2="350" stroke="#1976d2" stroke-width="2" marker-end="url(#arrowhead)"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'ArchitectureDiagram'
}
</script>

<style scoped>
.architecture-diagram {
  max-width: 100%;
  overflow-x: auto;
}

.architecture-diagram svg {
  min-width: 600px;
}
</style>
