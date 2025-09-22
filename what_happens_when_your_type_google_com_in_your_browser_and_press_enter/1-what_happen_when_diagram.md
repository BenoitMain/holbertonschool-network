![google_request_flow](https://github.com/user-attachments/assets/270769e5-62bd-4e6b-be48-06a70fde395a)
<?xml version="1.0" ?>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="1400" height="520">
	<defs>
		<style type="text/css">
    .node { fill: #f9f9f9; stroke: #333; stroke-width: 1.5; rx: 10; ry: 10; }
    .node-accent { fill: #eef6ff; stroke: #1f4b99; }
    .node-sec { fill: #eefaf1; stroke: #1d7a46; }
    .title { font-size: 20px; font-family: Arial, sans-serif; font-weight: bold; }
    .label { font-size: 14px; font-family: Arial, sans-serif; }
    .small { font-size: 12px; font-family: Arial, sans-serif; fill: #333; }
    .arrow { stroke: #333; stroke-width: 1.5; marker-end: url(#arrowhead); fill: none; }
    .dashed { stroke-dasharray: 5,5; }
    .note { font-size: 12px; font-family: Arial, sans-serif; fill: #1f4b99; }
</style>
		<marker id="arrowhead" markerWidth="10" markerHeight="7" refX="10" refY="3.5" orient="auto">
			<polygon points="0 0, 10 3.5, 0 7" fill="#333"/>
		</marker>
	</defs>
	<text x="20" y="30" class="title">HTTPS request flow when typing https://www.google.com and pressing Enter</text>
	<rect x="20" y="140" width="180" height="80" class="node-accent"/>
	<text x="110.0" y="177.0" class="label" text-anchor="middle">Client</text>
	<text x="110.0" y="195.0" class="label" text-anchor="middle">Browser</text>
	<rect x="240" y="140" width="180" height="80" class="node-accent"/>
	<text x="330.0" y="177.0" class="label" text-anchor="middle">DNS</text>
	<text x="330.0" y="195.0" class="label" text-anchor="middle">Resolver</text>
	<rect x="460" y="140" width="180" height="80" class="node-accent"/>
	<text x="550.0" y="177.0" class="label" text-anchor="middle">Server IP</text>
	<text x="550.0" y="195.0" class="label" text-anchor="middle">(A/AAAA record)</text>
	<rect x="680" y="140" width="180" height="80" class="node-sec"/>
	<text x="770.0" y="177.0" class="label" text-anchor="middle">Network</text>
	<text x="770.0" y="195.0" class="label" text-anchor="middle">Firewall</text>
	<rect x="900" y="140" width="180" height="80" class="node-sec"/>
	<text x="990.0" y="177.0" class="label" text-anchor="middle">Load</text>
	<text x="990.0" y="195.0" class="label" text-anchor="middle">Balancer</text>
	<rect x="1120" y="140" width="180" height="80" class="node"/>
	<text x="1210.0" y="177.0" class="label" text-anchor="middle">Web Server</text>
	<text x="1210.0" y="195.0" class="label" text-anchor="middle">(HTTPS, :443)</text>
	<rect x="1340" y="140" width="180" height="80" class="node"/>
	<text x="1430.0" y="177.0" class="label" text-anchor="middle">Application</text>
	<text x="1430.0" y="195.0" class="label" text-anchor="middle">Server</text>
	<rect x="1560" y="140" width="180" height="80" class="node"/>
	<text x="1650.0" y="177.0" class="label" text-anchor="middle">Database</text>
	<text x="1650.0" y="195.0" class="label" text-anchor="middle">Cluster</text>
	<text x="30" y="120" class="note">1) DNS resolution (google.com → IP)</text>
	<text x="690" y="120" class="note">2) Encrypted HTTPS over TLS (port 443)</text>
	<text x="910" y="100" class="note">3) Firewall then Load Balancer routing</text>
	<text x="1130" y="120" class="note">4) Web → App → DB</text>
	<line x1="200" y1="180.0" x2="240" y2="180.0" class="arrow"/>
	<text x="220.0" y="172.0" class="small" text-anchor="middle">Lookup google.com</text>
	<line x1="420" y1="180.0" x2="460" y2="180.0" class="arrow"/>
	<text x="440.0" y="172.0" class="small" text-anchor="middle">A/AAAA response</text>
	<line x1="640" y1="180.0" x2="680" y2="180.0" class="arrow"/>
	<text x="660.0" y="172.0" class="small" text-anchor="middle">TCP SYN → :443</text>
	<line x1="860" y1="180.0" x2="900" y2="180.0" class="arrow"/>
	<text x="880.0" y="172.0" class="small" text-anchor="middle">Allowed traffic</text>
	<line x1="1080" y1="180.0" x2="1120" y2="180.0" class="arrow"/>
	<text x="1100.0" y="172.0" class="small" text-anchor="middle">Distributes request</text>
	<line x1="1300" y1="180.0" x2="1340" y2="180.0" class="arrow"/>
	<text x="1320.0" y="172.0" class="small" text-anchor="middle">Forward over HTTPS/TLS</text>
	<line x1="1520" y1="180.0" x2="1560" y2="180.0" class="arrow"/>
	<text x="1540.0" y="172.0" class="small" text-anchor="middle">SQL/query</text>
	<line x1="1560" y1="280.0" x2="1520" y2="280.0" class="arrow dashed"/>
	<text x="1540.0" y="272.0" class="small" text-anchor="middle">DB rows</text>
	<line x1="1340" y1="280.0" x2="1300" y2="280.0" class="arrow dashed"/>
	<text x="1320.0" y="272.0" class="small" text-anchor="middle">HTML/template</text>
	<line x1="1120" y1="280.0" x2="1080" y2="280.0" class="arrow dashed"/>
	<text x="1100.0" y="272.0" class="small" text-anchor="middle">HTTP 200 OK</text>
	<line x1="900" y1="280.0" x2="860" y2="280.0" class="arrow dashed"/>
	<text x="880.0" y="272.0" class="small" text-anchor="middle">TLS</text>
	<line x1="680" y1="280.0" x2="640" y2="280.0" class="arrow dashed"/>
	<text x="660.0" y="272.0" class="small" text-anchor="middle">Stateful FW</text>
	<line x1="460" y1="280.0" x2="420" y2="280.0" class="arrow dashed"/>
	<text x="440.0" y="272.0" class="small" text-anchor="middle">(no DNS here)</text>
	<line x1="240" y1="280.0" x2="200" y2="280.0" class="arrow dashed"/>
	<text x="220.0" y="272.0" class="small" text-anchor="middle">Decrypted in browser</text>
	<text x="990" y="260" class="small" text-anchor="middle">🔐 TLS encryption end-to-end (client ↔ LB/web/app)</text>
	<text x="990.0" y="240" class="small" text-anchor="middle">Port: 443 (HTTPS)</text>
	<text x="1390" y="510" class="small" text-anchor="end">© Request Flow Diagram</text>
</svg>
