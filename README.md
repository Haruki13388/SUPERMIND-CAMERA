# SUPERMIND-CAMERA
import React, { useRef, useEffect } from "react";

export default function CameraFeed() {
  const videoRef = useRef(null);

  useEffect(() => {
    async function enableCamera() {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({ video: true });
        videoRef.current.srcObject = stream;
      } catch (err) {
        alert("Camera access denied or unavailable.");
      }
    }
    enableCamera();
  }, []);

  return (
    <div style={{
      border: "2px solid cyan",
      borderRadius: "16px",
      background: "#111927",
      display: "inline-block",
      padding: "1rem"
    }}>
      <video
        ref={videoRef}
        autoPlay
        width={480}
        height={360}
        style={{ borderRadius: "12px", boxShadow: "0 0 16px #0ff" }}
      />
      <div style={{ color: "#0ff", marginTop: "0.5rem", textAlign: "center" }}>Camera Active</div>
    </div>
  );
}import React, { useState } from "react";

export default function ChatUI() {
  const [messages, setMessages] = useState([
    { sender: "ai", text: "Hello! I am your AI Super Mind. How can I help you?" }
  ]);
  const [input, setInput] = useState("");

  function sendMessage(e) {
    e.preventDefault();
    if (!input.trim()) return;
    setMessages([...messages, { sender: "user", text: input }]);
    // Simulate AI response
    setTimeout(() => {
      setMessages(msgs => [
        ...msgs,
        { sender: "ai", text: "I am analyzing your request..." }
      ]);
    }, 800);
    setInput("");
  }

  return (
    <div style={{
      background: "#22262a",
      color: "#eee",
      borderRadius: "16px",
      padding: "1rem",
      width: "320px",
      boxShadow: "0 0 16px #0ff"
    }}>
      <div style={{ height: "160px", overflowY: "auto", marginBottom: "1rem" }}>
        {messages.map((msg, i) => (
          <div key={i} style={{
            textAlign: msg.sender === "user" ? "right" : "left",
            margin: "0.25rem 0"
          }}>
            <span style={{
              background: msg.sender === "user" ? "#0ff2" : "#0ff1",
              padding: "0.5rem 1rem",
              borderRadius: "12px",
              display: "inline-block"
            }}>{msg.text}</span>
          </div>
        ))}
      </div>
      <form onSubmit={sendMessage} style={{ display: "flex" }}>
        <input
          value={input}
          onChange={e => setInput(e.target.value)}
          placeholder="Type here..."
          style={{
            flex: 1,
            borderRadius: "8px 0 0 8px",
            padding: "0.5rem",
            border: "none",
            outline: "none"
          }}
        />
        <button
          type="submit"
          style={{
            background: "#0ff",
            color: "#111927",
            border: "none",
            borderRadius: "0 8px 8px 0",
            padding: "0 1rem",
            cursor: "pointer"
          }}>
          Send
        </button>
      </form>
    </div>
  );
}import React, { useRef, useEffect } from "react";
export default function CameraFeed() {
  const videoRef = useRef();
  useEffect(() => {
    navigator.mediaDevices.getUserMedia({ video: true })
      .then(stream => { if(videoRef.current) videoRef.current.srcObject = stream; });
  }, []);
  return <video ref={videoRef} autoPlay width={480} height={360} />;
}import React from "react";
export default function ObjectScanner() {
  return <div>Object Scanner (AI object recognition coming soon)</div>;
}import React from "react";
export default function PersonRecognizer() {
  return <div>Person Recognizer (Face recognition and info retrieval coming soon)</div>;
}import React, { useState } from "react";
export default function VisionModes({ onModeChange }) {
  const [mode, setMode] = useState("normal");
  function handleChange(e) {
    setMode(e.target.value);
    onModeChange && onModeChange(e.target.value);
  }
  return (
    <select value={mode} onChange={handleChange}>
      <option value="normal">Normal</option>
      <option value="thermal">Thermal</option>
      <option value="gray">Gray</option>
      <option value="night">Night Vision</option>
      <option value="satellite">Satellite</option>
    </select>
  );
}import React from "react";
export default function ProximitySensor() {
  return <div>Proximity Sensor (Nearby people/phone detection coming soon)</div>;
}import React from "react";
export default function NotificationPanel() {
  return <div>Notifications (Alerts about new detections will show here)</div>;
}import React from "react";
export default function VoiceChatButton() {
  return <button>🎤 Voice Chat</button>;
}import React, { useState } from "react";
export default function ChatUI() {
  const [messages, setMessages] = useState([{sender:'ai',text:'Hello!'}]);
  const [input, setInput] = useState("");
  function send(e) {
    e.preventDefault();
    setMessages(m => [...m, {sender:'user',text:input}]);
    setInput("");
  }
  return (
    <div>import React from "react";

export default function ArtDesign() {
  return (
    <div style={{
      width: "100%",
      margin: "32px 0",
      display: "flex",
      justifyContent: "center",
      alignItems: "center"
    }}>
      <div style={{
        background: "linear-gradient(90deg, #00fff7 0%, #6a5acd 100%)",
        borderRadius: "24px",
        boxShadow: "0 0 32px #0ff8, 0 0 64px #6a5acd44",
        padding: "2rem 4rem",
        textAlign: "center",
        border: "2px solid #0ff",
        fontFamily: "Orbitron, 'Segoe UI', Arial, sans-serif",
        color: "#fff",
        fontSize: "2.2rem",
        letterSpacing: "0.08em",
        textTransform: "uppercase",
        textShadow: "0 0 8px #0ff, 0 0 32px #6a5acd"
      }}>
        <span style={{
          background: "rgba(0,255,247,0.13)",
          padding: "0.25em 1em",
          borderRadius: "14px",
          boxShadow: "0 0 16px #0ff6"
        }}>
          FUTURISTIC UI ART DESIGN
        </span>
      </div>
    </div>
  );
}import React, { useState } from "react";

export default function DistanceAdjuster({ onChange }) {
  const [distance, setDistance] = useState(5);

  const handleChange = (e) => {
    const value = e.target.value;
    setDistance(value);
    if (onChange) onChange(value);
  };

  return (
    <div style={{
      margin: "2rem 0",
      width: "320px",
      padding: "1.5rem",
      background: "rgba(10, 30, 40, 0.85)",
      borderRadius: "18px",
      boxShadow: "0 0 24px #0ff4",
      border: "2px solid #0ff8",
      display: "flex",
      flexDirection: "column",
      alignItems: "center"
    }}>
      <label
        htmlFor="distance-slider"
        style={{
          color: "#0ff",
          fontFamily: "Orbitron, 'Segoe UI', Arial, sans-serif",
          fontSize: "1.1rem",
          marginBottom: "1.2rem",
          letterSpacing: "0.07em"
        }}
      >
        Detection Distance: <span style={{
          color: "#fff",
          background: "#0ff5",
          padding: "0.15em 0.8em",
          borderRadius: "10px",
          marginLeft: "0.5em"
        }}>{distance} m</span>
      </label>
      <input
        id="distance-slider"
        type="range"
        min="1"
        max="20"
        value={distance}
        onChange={handleChange}
        style={{
          width: "90%",
          accentColor: "#0ff",
          background: "transparent",
          marginBottom: "0.7rem"
        }}
      />
      <div style={{
        width: "88%",
        display: "flex",
        justifyContent: "space-between",
        color: "#0ffb",
        fontSize: "0.92rem"
      }}>
        <span>1m</span>
        <span>20m</span>
      </div>
    </div>
  );
}
      <div style={{height:100,overflow:'auto'}}>
        {messages.map((m,i) => <div key={i}><b>{m.sender}:</b> {m.text}</div>)}
      </div>
      <form onSubmit={send}>
        <input value={input} onChange={e=>setInput(e.target.value)} />
        <button>Send</button>
      </form>
    </div>
  );
}import React, { useState } from "react";
import CameraFeed from "./components/CameraFeed";
import ObjectScanner from "./components/ObjectScanner";
import PersonRecognizer from "./components/PersonRecognizer";
import VisionModes from "./components/VisionModes";
import ProximitySensor from "./components/ProximitySensor";
import NotificationPanel from "./components/NotificationPanel";
import VoiceChatButton from "./components/VoiceChatButton";
import ChatUI from "./components/ChatUI";
import ArtDesign from "./components/ArtDesign";
import DistanceAdjuster from "./components/DistanceAdjuster";

const appBg = {
  minHeight: "100vh",
  width: "100vw",
  background: "radial-gradient(ellipse at 60% 20%, #1a2337 0%, #010510 100%)",
  color: "#0ff",
  fontFamily: "Orbitron, 'Segoe UI', Arial, sans-serif",
  display: "flex",
  flexDirection: "column",
  alignItems: "center",
  paddingBottom: "2rem"
};

const dashboardGrid = {
  display: "grid",
  gridTemplateColumns: "repeat(auto-fit, minmax(340px, 1fr))",
  gap: "2.5rem",
  width: "98%",
  maxWidth: "1200px",
  margin: "0 auto"
};

export default function App() {
  const [visionMode, setVisionMode] = useState("normal");
  const [distance, setDistance] = useState(5);

  return (
    <div style={appBg}>
      <h1 style={{
        fontSize: "2.7rem",
        margin: "2.5rem 0 1rem 0",
        textShadow: "0 0 12px #0ff, 0 0 32px #6a5acd"
      }}>
        AI Super Mind Robot Cam
      </h1>
      <ArtDesign />

      {/* Controls row */}
      <div style={{
        display: "flex",
        flexWrap: "wrap",
        gap: "2rem",
        marginBottom: "2rem",
        justifyContent: "center"
      }}>
        <VisionModes onModeChange={setVisionMode} />
        <DistanceAdjuster onChange={setDistance} />
        <VoiceChatButton />
      </div>

      {/* Main dashboard grid */}
      <div style={dashboardGrid}>
        <div>
          <CameraFeed />
          <NotificationPanel />
        </div>
        <div>
          <ObjectScanner />
          <PersonRecognizer />
          <ProximitySensor />
        </div>
        <ChatUI />
      </div>

      <footer style={{
        marginTop: "2.5rem",
        color: "#57e6e6",
        fontWeight: 300,
        fontSize: "1rem",
        letterSpacing: ".06em"
      }}>
        Vision Mode: <b>{visionMode}</b> &nbsp;|&nbsp; Detection Distance: <b>{distance}m</b>
      </footer>
    </div>
  );
}
