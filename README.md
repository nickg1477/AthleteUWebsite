// LandingPage.jsx – Self‑contained React component (no external UI libs required)
// Built for a standard Vite or Create‑React‑App setup with TailwindCSS.

import { useState } from "react";
import { motion } from "framer-motion";

export default function LandingPage() {
  const [tier, setTier] = useState("athlete");

  return (
    <main className="font-sans text-slate-100 bg-[#003B7A] min-h-screen w-full overflow-x-hidden">
      {/* HERO */}
      <section className="relative flex flex-col items-center justify-center text-center pt-24 pb-32 px-6 md:px-12">
        <motion.h1
          initial={{ opacity: 0, y: 40 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6 }}
          className="text-4xl md:text-6xl font-extrabold tracking-tight max-w-5xl leading-tight"
        >
          Empowering Coaches. <br className="hidden sm:inline" /> Elevating Athletes.
        </motion.h1>
        <p className="mt-6 max-w-xl text-lg md:text-xl text-slate-200">
          Sport‑specific, science‑backed programs designed by CSCS‑certified Division‑I strength
          coaches—accessible to every under‑recruited athlete.
        </p>
        <motion.button
          whileHover={{ scale: 1.05 }}
          whileTap={{ scale: 0.95 }}
          className="mt-8 bg-[#1877F2] hover:bg-[#0A66C2] text-white font-semibold py-3 px-8 rounded-2xl shadow-xl"
        >
          Join the Waitlist
        </motion.button>
        <span className="mt-3 text-sm text-slate-300">Launching soon • $17.99/mo after 3‑day free trial</span>
      </section>

      {/* FEATURES */}
      <section className="bg-[#002C5A] py-20 px-6 md:px-12">
        <div className="max-w-6xl mx-auto grid md:grid-cols-3 gap-12 text-center">
          {[
            {
              title: "Sport‑Specific Workouts",
              icon: "🏆",
              desc: "Adaptive blocks tuned to the movement patterns & energy systems of your sport.",
            },
            {
              title: "CSCS Coach Marketplace",
              icon: "📚",
              desc: "Every creator is a certified strength & conditioning specialist from Division‑I athletics.",
            },
            {
              title: "Real‑Time Progress",
              icon: "📈",
              desc: "Load velocity, readiness scores, and leaderboards keep you accountable and injury‑free.",
            },
          ].map((f, i) => (
            <motion.div
              key={i}
              initial={{ opacity: 0, y: 20 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ delay: i * 0.1 }}
              className="bg-[#003B7A] rounded-2xl p-8 shadow-lg flex flex-col items-center"
            >
              <span className="text-4xl">{f.icon}</span>
              <h3 className="mt-4 text-xl font-bold">{f.title}</h3>
              <p className="mt-2 text-sm text-slate-300">{f.desc}</p>
            </motion.div>
          ))}
        </div>
      </section>

      {/* PRICING TOGGLE */}
      <section className="py-20 px-6 md:px-12 bg-[#003B7A]">
        <div className="max-w-3xl mx-auto text-center">
          <h2 className="text-3xl font-extrabold">Simple, Honest Pricing</h2>
          <div className="flex justify-center mt-6 gap-4">
            {[
              { id: "athlete", label: "Athletes" },
              { id: "coach", label: "Coaches" },
            ].map((t) => (
              <button
                key={t.id}
                onClick={() => setTier(t.id)}
                className={`px-6 py-2 rounded-full border transition-colors ${
                  tier === t.id ? "bg-[#1877F2] border-transparent" : "border-slate-400"
                }`}
              >
                {t.label}
              </button>
            ))}
          </div>
          {tier === "athlete" ? (
            <div className="mt-8 text-lg">
              <span className="text-4xl font-extrabold">$17.99</span>
              <span className="ml-1">/ month</span>
              <p className="mt-2 text-slate-300">First 3 days are free • Cancel anytime</p>
            </div>
          ) : (
            <div className="mt-8 text-lg">
              <span className="text-2xl font-extrabold">Free to publish</span>
              <p className="mt-2 text-slate-300">Earn royalties on every program download</p>
            </div>
          )}
        </div>
      </section>

      {/* JOIN WAITLIST */}
      <section className="bg-[#002C5A] py-20 px-6 md:px-12">
        <div className="max-w-xl mx-auto text-center">
          <h2 className="text-3xl font-extrabold">Be first in line</h2>
          <p className="mt-2 text-slate-300">
            Drop your email and we’ll notify you the moment Athlete University hits the App Store.
          </p>
          <form
            action="https://your-waitlist-endpoint.com" // replace with real endpoint
            method="POST"
            className="mt-8 flex flex-col sm:flex-row gap-4"
          >
            <input
              type="email"
              name="email"
              required
              placeholder="you@example.com"
              className="flex-1 px-5 py-3 rounded-full text-black focus:outline-none"
            />
            <button
              type="submit"
              className="bg-[#FFD700] hover:bg-yellow-400 text-[#003B7A] font-bold px-6 py-3 rounded-full shadow-lg"
            >
              Join Waitlist
            </button>
          </form>
        </div>
      </section>

      {/* FOOTER */}
      <footer className="bg-[#003B7A] py-8 px-6 md:px-12 text-center text-sm text-slate-300">
        <div className="flex justify-center gap-6 mb-4">
          <a href="https://instagram.com/yourhandle" target="_blank" rel="noopener noreferrer" className="hover:text-white">
            <span className="sr-only">Instagram</span>
            <svg aria-hidden="true" focusable="false" className="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M7.75 2h8.5A5.76 5.76 0 0 1 22 7.75v8.5A5.76 5.76 0 0 1 16.25 22h-8.5A5.76 5.76 0 0 1 2 16.25v-8.5A5.76 5.76 0 0 1 7.75 2zm0 2A3.75 3.75 0 0 0 4 7.75v8.5A3.75 3.75 0 0 0 7.75 20h8.5A3.75 3.75 0 0 0 20 16.25v-8.5A3.75 3.75 0 0 0 16.25 4h-8.5zM12 7a5 5 0 1 1 0 10 5 5 0 0 1 0-10zm0 2a3 3 0 1 0 0 6 3 3 0 0 0 0-6zm5.5-.25a1.25 1.25 0 1 1-2.5 0 1.25 1.25 0 0 1 2.5 0z" />
            </svg>
          </a>
          <a href="https://tiktok.com/@yourhandle" target="_blank" rel="noopener noreferrer" className="hover:text-white">
            <span className="sr-only">TikTok</span>
            <svg aria-hidden="true" focusable="false" className="h-6 w-6" fill="currentColor" viewBox="0 0 24 24">
              <path d="M16 8.245c1.992 1.295 3.498 1.402 4 1.408v2.98c-.533.048-2.32-.035-4-1.168V16.8c0 4.5-2.7 6.2-5.207 6.2a5.34 5.34 0 0 1 0-10.68c.243 0 .48.02.707.058V14.6c-.227-.028-.464-.048-.707-.048a2.4 2.4 0 0 0 0 4.8c1.6 0 2.4-1 2.4-2.4V2h2.807c.375 2.925 2.115 5.1 4.393 6.245H16z" />
            </svg>
          </a>
        </div>
        <p>© {new Date().getFullYear()} Athlete University. All rights reserved.</p>
      </footer>
    </main>
  );
}

