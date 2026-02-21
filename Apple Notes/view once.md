To compromise the WhatsApp Web client and bypass View Once restrictions, the attacker would modify or instrument the web client to:
	1.	**Intercept Decrypted Content**:
	•	Inject JavaScript into the web client (via browser extension, proxy, or developer console) to hook into the DOM rendering functions.
	•	Extract the image/video blob before or during rendering.
	•	Save or clone the media before the “view once” mechanism triggers deletion.
	2.	**Bypass Deletion Hooks**:
	•	Patch or override JavaScript responsible for removing the View Once message after viewing.
	•	Prevent event handlers from executing (e.g., disabling onload or onclose cleanup logic).
	3.	**Delay State Change**:
	•	Freeze the frontend state or DOM mutations after loading the media.
	•	Prevent the message status from being marked as “viewed” by intercepting the status update request to the phone.
	4.	**Capture Media from Memory**:
	•	Dump in-memory blobs (e.g., URL.createObjectURL() results).
	•	Read internal React component state if exposed via dev tools or overridden React DevTools.
	5.	**Network Proxy (advanced)**:
	•	Man-in-the-middle the WebSocket channel via a local proxy with certificate injection.
	•	Extract plaintext payloads if the client device is already decrypted and forwarding them.
	•	Requires full control of the local device and session.
	6.	**Automation Tools**:
	•	Use browser automation (e.g., Puppeteer) to hook into render and download routines programmatically.
	•	Capture screenshots, network payloads, or raw media content.

Summary: View Once media is decrypted on the phone and forwarded in plaintext to the browser. Any control over the browser’s JavaScript context, memory, or network channel allows an attacker to intercept, clone, or delay deletion of the content.