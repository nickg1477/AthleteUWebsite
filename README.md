# AthleteUWebsite
First time coding a websiteimport { useState } from "react";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Tabs, TabsList, TabsTrigger } from "@/components/ui/tabs";
import { motion } from "framer-motion";
import { Activity, ShieldCheck, TrendingUp, Instagram } from "lucide-react";

export default function LandingPage() {
  const [pricingTier, setPricingTier] = useState("athlete");

  return (
    <div className="font-sans text-gray-100 bg-[#003B7A] w-full overflow-x-hidden scroll-smooth">
      {/* NAVBAR */}
      <nav className="fixed top-0 left-0 w-full z-50 backdrop-blur-sm/10 bg-[#003B7A]/60 border-b border-white/10">
        <div className="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
          <span className="text-2xl font-extrabold tracking-tight">Athlete&nbsp;U</span>
          <div className="flex items-center gap-4">
            <Button asChild variant="outline" size="sm" className="border-white/20 hover:bg-white/10">
              <a href="#waitlist">Join Waitlist</a>
            </Button>
            <Button asChild variant="outline" size="icon" className="border-white/20 hover:bg-white/10">
              <a href="https://instagram.com/athleteuapp" target="_blank" rel="noopener" aria-label="Instagram">
                <Instagram className="h-4 w-4" />
              </a>
            </Button>
            <Button asChild variant="outline" size="icon" className="border-white/20 hover:bg-white/10">
              <a href="https://tiktok.com/@athleteuapp" target="_blank" rel="noopener" aria-label="TikTok">
                {/* simple TikTok note icon using SVG */}
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" className="h-4 w-4 fill-current">
                  <path d="M12 2c1.1 0 2 .9 2 2v11.56a3.44 3.44 0 1 1-2-3.15V6h2.79a4 4 0 0 0 3.21 1.65V9a6 6 0 1 1-6-7z" />
                </svg>
              </a>
            </Button>
          </div>
        </div>
      </nav>

      {/* HERO */}
      <section className="relative flex flex-col items-center justify-center pt-32 pb-24 bg-[url('/hero-gym.mp4')] bg-cover bg-center text-center">
        <motion.h1 initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6 }} className="text-4xl sm:text-6xl font-extrabold leading-tight mb-4 max-w-4xl">
          Empowering Coaches. Elevating Athletes.
        </motion.h1>
        <p className="text-lg sm:text-xl max-w-2xl mb-8 text-white/80">
          Science‑backed, sport‑specific strength programs crafted by NCAA Division I CSCS‑certified performance coaches—delivered straight to your pocket.
        </p>
        <Button size="lg" className="text-lg px-8 py-6" asChild>
          <a href="#waitlist">Claim 3‑Day Free Trial</a>
        </Button>
        <p className="mt-4 text-sm text-white/70">$17.99 / month • cancel anytime after free trial</p>
      </section>

      {/* FEATURE STRIP */}
      <section className="py-20 bg-[#002d5b]">
        <div className="max-w-6xl mx-auto grid md:grid-cols-3 gap-8 px-6">
          {[
            {
              icon: Activity,
              title: "Sport‑Specific Blocks",
              copy: "Every program adapts to your position, season phase, and readiness scores."
            },
            {
              icon: ShieldCheck,
              title: "CSCS‑Certified Coaches",
              copy: "Built by the same Division I specialists trusted by elite programs."
            },
            {
              icon: TrendingUp,
              title: "Real‑Time Insights",
              copy: "Velocity‑based feedback and load tracking keep you progressing safely."
            }
          ].map((f, i) => (
            <motion.div key={i} initial={{ opacity: 0, y: 20 }} whileInView={{ opacity: 1, y: 0 }} transition={{ duration: 0.4, delay: i * 0.15 }} viewport={{ once: true }}>
              <Card className="bg-[#003B7A] border-white/10">
                <CardHeader className="flex flex-col items-center gap-4 py-10">
                  <f.icon className="h-10 w-10 text-yellow-400" />
                  <CardTitle className="text-xl text-yellow-400 text-center">
                    {f.title}
                  </CardTitle>
                </CardHeader>
                <CardContent className="text-center text-white/80 pb-10">
                  {f.copy}
                </CardContent>
              </Card>
            </motion.div>
          ))}
        </div>
      </section>

      {/* PRICING & TRIAL */}
      <section id="pricing" className="py-24 bg-[#003B7A] relative">
        <div className="max-w-4xl mx-auto text-center px-6">
          <h2 className="text-3xl sm:text-4xl font-bold mb-6">Founders Launch Pricing</h2>
          <Tabs defaultValue="athlete" className="mx-auto w-full max-w-md mb-10">
            <TabsList>
              <TabsTrigger value="athlete" onClick={() => setPricingTier("athlete")}>Athletes</TabsTrigger>
              <TabsTrigger value="coach" onClick={() => setPricingTier("coach")}>Coaches</TabsTrigger>
            </TabsList>
          </Tabs>

          <Card className="mx-auto max-w-md bg-[#002d5b] border-white/10">
            <CardHeader>
              <CardTitle className="text-2xl">
                {pricingTier === "athlete" ? "$17.99 / month" : "Build Free • Earn Royalties"}
              </CardTitle>
            </CardHeader>
            <CardContent>
              <ul className="space-y-3 text-left list-disc list-inside text-white/80">
                {pricingTier === "athlete" ? (
                  <>
                    <li>First 3 days free — cancel anytime</li>
                    <li>Unlimited sport‑specific workouts</li>
                    <li>Readiness & progress analytics</li>
                  </>
                ) : (
                  <>
                    <li>Create unlimited programs</li>
                    <li>Publish to the marketplace in minutes</li>
                    <li>Earn lifetime royalties per download</li>
                  </>
                )}
              </ul>
              <Button size="lg" className="w-full mt-8" asChild>
                <a href="#waitlist">{pricingTier === "athlete" ? "Start Free Trial" : "Apply as Coach"}</a>
              </Button>
            </CardContent>
          </Card>
        </div>
      </section>

      {/* WAITLIST */}
      <section id="waitlist" className="py-24 bg-[#002d5b] relative">
        <div className="max-w-3xl mx-auto text-center px-6">
          <h2 className="text-3xl sm:text-4xl font-bold mb-6">Join the Waitlist</h2>
          <p className="text-lg mb-6 text-white/80 max-w-xl mx-auto">
            Be first in line when Athlete University drops on the App Store — plus snag exclusive launch swag.
          </p>
          <form className="flex flex-col sm:flex-row gap-4 justify-center">
            <Input type="email" placeholder="you@example.com" required className="bg-white text-[#003B7A]" />
            <Button size="lg" type="submit" className="px-8 py-6">Get Early Access</Button>
          </form>
        </div>
      </section>

      {/* FOOTER */}
      <footer className="bg-[#003B7A] border-t border-white/10 py-10 text-center text-sm text-white/60">
        <p>&copy; {new Date().getFullYear()} Athlete University. All rights reserved.</p>
      </footer>
    </div>
  );
}

