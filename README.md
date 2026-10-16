<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 150" width="1000" height="150" role="img" aria-label="Build, Measure, Optimize, Repeat">
  <defs>
    <linearGradient id="lane" gradientUnits="userSpaceOnUse" x1="200" y1="0" x2="800" y2="0">
      <stop offset="0" stop-color="#7F00FF"/>
      <stop offset="1" stop-color="#00D4FF"/>
    </linearGradient>
    <filter id="soft" x="-100%" y="-100%" width="300%" height="300%">
      <feGaussianBlur stdDeviation="3"/>
    </filter>
    <!-- loop: forward lane (bottom) → right turn → return lane (top) → left turn. Length ≈ 1357 -->
    <path id="loop" d="M200 90 L800 90 A25 25 0 0 0 800 40 L200 40 A25 25 0 0 0 200 90 Z"/>
  </defs>

  <style>
    .sans { font-family: 'Segoe UI','Inter',-apple-system,BlinkMacSystemFont,Helvetica,Arial,sans-serif; }
    .back { stroke-dasharray: 3 9; animation: back 1.2s linear infinite; }
    @keyframes back { to { stroke-dashoffset: 24; } }
    @media (prefers-reduced-motion: reduce) { * { animation: none !important; } }
  </style>

  <!-- return lane -->
  <path d="M800 90 A25 25 0 0 0 800 40 L200 40 A25 25 0 0 0 200 90" fill="none" stroke="#8B949E" stroke-opacity="0.45" stroke-width="1.5" class="back"/>

  <!-- forward lane -->
  <line x1="200" y1="90" x2="800" y2="90" stroke="url(#lane)" stroke-width="3" stroke-linecap="round"/>

  <!-- packet with trailing comet -->
  <g fill="#00D4FF">
    <circle r="3" opacity="0.25"><animateMotion dur="6s" repeatCount="indefinite" begin="-5.84s"><mpath href="#loop"/></animateMotion></circle>
    <circle r="3.5" opacity="0.45"><animateMotion dur="6s" repeatCount="indefinite" begin="-5.92s"><mpath href="#loop"/></animateMotion></circle>
    <circle r="9" opacity="0.55" filter="url(#soft)"><animateMotion dur="6s" repeatCount="indefinite" begin="0s"><mpath href="#loop"/></animateMotion></circle>
    <circle r="4.5" fill="#FFFFFF"><animateMotion dur="6s" repeatCount="indefinite" begin="0s"><mpath href="#loop"/></animateMotion></circle>
  </g>

  <!-- stage nodes: each ring fires as the packet passes (arrival = distance / 1357 of a 6s loop) -->
  <g fill="none" stroke="#00D4FF" stroke-width="2">
    <circle cx="200" cy="90" r="9" opacity="0">
      <animate attributeName="r" dur="6s" repeatCount="indefinite" values="9;9;22;22" keyTimes="0;0.001;0.12;1"/>
      <animate attributeName="opacity" dur="6s" repeatCount="indefinite" values="0;0.9;0;0" keyTimes="0;0.001;0.12;1"/>
    </circle>
    <circle cx="400" cy="90" r="9" opacity="0">
      <animate attributeName="r" dur="6s" repeatCount="indefinite" values="9;9;22;22" keyTimes="0;0.147;0.267;1"/>
      <animate attributeName="opacity" dur="6s" repeatCount="indefinite" values="0;0.9;0;0" keyTimes="0;0.147;0.267;1"/>
    </circle>
    <circle cx="600" cy="90" r="9" opacity="0">
      <animate attributeName="r" dur="6s" repeatCount="indefinite" values="9;9;22;22" keyTimes="0;0.295;0.415;1"/>
      <animate attributeName="opacity" dur="6s" repeatCount="indefinite" values="0;0.9;0;0" keyTimes="0;0.295;0.415;1"/>
    </circle>
    <circle cx="800" cy="90" r="9" opacity="0">
      <animate attributeName="r" dur="6s" repeatCount="indefinite" values="9;9;22;22" keyTimes="0;0.442;0.562;1"/>
      <animate attributeName="opacity" dur="6s" repeatCount="indefinite" values="0;0.9;0;0" keyTimes="0;0.442;0.562;1"/>
    </circle>
  </g>
  <g stroke="#FFFFFF" stroke-width="2.5">
    <circle cx="200" cy="90" r="8" fill="#7F00FF"/>
    <circle cx="400" cy="90" r="8" fill="#5A35FF"/>
    <circle cx="600" cy="90" r="8" fill="#2F6BFF"/>
    <circle cx="800" cy="90" r="8" fill="#00B8E6"/>
  </g>

  <g class="sans" font-size="15" font-weight="700" text-anchor="middle" fill="#8B949E">
    <text x="200" y="126">Build</text>
    <text x="400" y="126">Measure</text>
    <text x="600" y="126">Optimize</text>
    <text x="800" y="126">Repeat</text>
  </g>
</svg>
