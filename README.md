import { useState } from "react";
import { Github, Mail, Globe, Linkedin, MapPin, Download, ArrowRight, Instagram, FileText, Video, Mic, Calendar } from "lucide-react";
import { Button } from "@/components/ui/button";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

// ————————————————————————————————————————————————————————————
// Modern "About Me" — single-file React page
// - TailwindCSS + shadcn/ui
// - Dark/light friendly
// - Replace placeholders ({{ ... }}) with your info
// - Exported as default component so it can render in the canvas
// ————————————————————————————————————————————————————————————

export default function AboutMe() {
  const [year] = useState(new Date().getFullYear());

  const skills = [
    { group: "Languages", items: ["Korean (Native)", "English", "Indonesian (basic)"] },
    { group: "Tech", items: ["Python", "Spring Boot", "TypeScript", "React", "PostgreSQL", "Tailwind"] },
    { group: "AI/ML", items: ["OpenAI", "Prompt Design", "LLM Orchestration", "k6/Gatling (SSE)"] },
    { group: "EdTech", items: ["Curriculum Design", "AI Literacy", "Assessment", "CSR Partnerships"] },
  ];

  const links = [
    { label: "GitHub", icon: <Github className="h-4 w-4"/>, href: "https://github.com/{{your-github}}" },
    { label: "LinkedIn", icon: <Linkedin className="h-4 w-4"/>, href: "https://linkedin.com/in/{{your-linkedin}}" },
    { label: "Website", icon: <Globe className="h-4 w-4"/>, href: "https://{{your-site}}" },
    { label: "Instagram", icon: <Instagram className="h-4 w-4"/>, href: "https://instagram.com/{{your-instagram}}" },
    { label: "Email", icon: <Mail className="h-4 w-4"/>, href: "mailto:office@ppleedu.org" },
  ];

  const projects = [
    {
      title: "Dream AI Studio",
      desc: "학생이 상상한 이야기와 이미지를 AI로 함께 완성해 동화책으로 제작하는 창작 플랫폼.",
      chips: ["GenAI", "Storybook", "Education"],
      href: "https://{{demo-or-repo}}"
    },
    {
      title: "AI Creator (Curriculum)",
      desc: "초등~성인 대상 AI 리터러시/창작 커리큘럼. 실습 중심, 지역 기반 주제 연계.",
      chips: ["Curriculum", "Workshop", "Assessment"],
      href: "https://{{docs-or-deck}}"
    },
    {
      title: "SSE Load Test",
      desc: "k6 기반 SSE 채팅 부하 테스트 스크립트 및 지표 대시보드 구축.",
      chips: ["k6", "SSE", "DevOps"],
      href: "https://{{repo-link}}"
    }
  ];

  const timeline = [
    { year: "2025", text: "전북 청소년 Dream AI 리터러시 운영 · 콘테스트/전시 연계" },
    { year: "2024", text: "Dream AI Studio 베타 · 교육 프로그램 다지역 확장" },
    { year: "2023", text: "AI 문해/창작 수업 다수 운영 · CSR 파트너십 시작" },
  ];

  return (
    <div className="min-h-screen bg-gradient-to-b from-background to-muted/30 text-foreground selection:bg-primary/20">
      {/* Hero */}
      <section className="container mx-auto px-4 pt-16 pb-10">
        <div className="grid gap-8 lg:grid-cols-3 items-center">
          <div className="lg:col-span-2 space-y-4">
            <div className="inline-flex items-center gap-2 rounded-full border px-3 py-1 text-sm">
              <MapPin className="h-4 w-4" /> 서울, 대한민국
            </div>
            <h1 className="text-4xl md:text-5xl font-bold tracking-tight">
              배성문(혁준) · AI 교육/플랫폼 리더
            </h1>
            <p className="text-muted-foreground text-lg max-w-2xl">
              피플에듀에서 AI 리터러시/창작 교육과 <span className="font-medium">Dream AI Studio</span>를 만들고 운영합니다.
              아이들과 성인 학습자가 모두 창작의 즐거움을 느끼도록, 기술과 교육의 간극을 잇습니다.
            </p>
            <div className="flex flex-wrap gap-2">
              <Badge variant="secondary">AI Literacy</Badge>
              <Badge variant="secondary">EdTech</Badge>
              <Badge variant="secondary">GenAI Storybook</Badge>
              <Badge variant="secondary">Curriculum Design</Badge>
            </div>
            <div className="flex flex-wrap gap-2 pt-2">
              {links.map((l) => (
                <Button key={l.label} asChild variant="outline" size="sm">
                  <a href={l.href} target="_blank" rel="noreferrer" className="inline-flex items-center gap-2">
                    {l.icon} {l.label}
                  </a>
                </Button>
              ))}
              <Button variant="default" size="sm" className="gap-2" asChild>
                <a href="/assets/Resume_KR.pdf" target="_blank" rel="noreferrer">
                  <Download className="h-4 w-4" /> 이력서
                </a>
              </Button>
            </div>
          </div>
          <div className="lg:justify-self-end">
            <div className="relative w-44 h-44 md:w-56 md:h-56 mx-auto rounded-2xl overflow-hidden shadow-xl ring-1 ring-border">
              <picture>
                <source media="(prefers-color-scheme: dark)" srcSet="/assets/profile-dark.png" />
                <img src="/assets/profile-light.png" alt="Profile" className="w-full h-full object-cover" />
              </picture>
            </div>
          </div>
        </div>
      </section>

      {/* Highlights */}
      <section className="container mx-auto px-4 pb-8">
        <div className="grid gap-4 md:grid-cols-3">
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base">현재</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">
              피플에듀 교육사업팀 팀장 · Dream AI Studio 기획/운영 · 지역 연계 AI 창작 수업
            </CardContent>
          </Card>
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base">관심사</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">
              생성형 AI 응용, 스토리텔링 교육, 사회공헌 연계, 인도네시아 현지 협력
            </CardContent>
          </Card>
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base">협업</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">
              커리큘럼 공동개발, 지역/기업 CSR 프로그램, 전시/행사, 파일럿 수업
            </CardContent>
          </Card>
        </div>
      </section>

      {/* Projects */}
      <section className="container mx-auto px-4 py-6">
        <div className="flex items-center justify-between mb-4">
          <h2 className="text-2xl font-semibold">대표 프로젝트</h2>
          <Button asChild variant="ghost" size="sm" className="gap-1">
            <a href="https://github.com/{{your-github}}?tab=repositories" target="_blank" rel="noreferrer">
              더 보기 <ArrowRight className="h-4 w-4" />
            </a>
          </Button>
        </div>
        <div className="grid gap-4 md:grid-cols-3">
          {projects.map((p) => (
            <Card key={p.title} className="hover:shadow-lg transition-shadow">
              <CardHeader>
                <CardTitle className="text-lg">{p.title}</CardTitle>
              </CardHeader>
              <CardContent>
                <p className="text-sm text-muted-foreground mb-3">{p.desc}</p>
                <div className="flex flex-wrap gap-2 mb-3">
                  {p.chips.map((c) => (
                    <Badge key={c} variant="outline">{c}</Badge>
                  ))}
                </div>
                <Button asChild size="sm" variant="outline">
                  <a href={p.href} target="_blank" rel="noreferrer">자세히 보기</a>
                </Button>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Skills */}
      <section className="container mx-auto px-4 py-6">
        <h2 className="text-2xl font-semibold mb-4">보유 스킬</h2>
        <div className="grid gap-4 md:grid-cols-2">
          {skills.map((s) => (
            <Card key={s.group}>
              <CardHeader className="pb-2"><CardTitle className="text-base">{s.group}</CardTitle></CardHeader>
              <CardContent className="flex flex-wrap gap-2">
                {s.items.map((i) => (
                  <Badge key={i} variant="secondary">{i}</Badge>
                ))}
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Talks & Media */}
      <section className="container mx-auto px-4 py-6">
        <h2 className="text-2xl font-semibold mb-4">강연 · 미디어</h2>
        <div className="grid gap-4 md:grid-cols-3">
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base flex items-center gap-2"><Mic className="h-4 w-4"/> 강연</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">AI 리터러시, 생성형 AI 교육, 지역 연계 창작</CardContent>
          </Card>
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base flex items-center gap-2"><Video className="h-4 w-4"/> 유튜브</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">교육 사례, 작품 전시, 튜토리얼</CardContent>
          </Card>
          <Card>
            <CardHeader className="pb-2"><CardTitle className="text-base flex items-center gap-2"><FileText className="h-4 w-4"/> 아티클</CardTitle></CardHeader>
            <CardContent className="text-sm text-muted-foreground">블로그/뉴스레터: Dream AI Studio 인사이트</CardContent>
          </Card>
        </div>
      </section>

      {/* Timeline */}
      <section className="container mx-auto px-4 py-6">
        <h2 className="text-2xl font-semibold mb-4">타임라인</h2>
        <div className="relative pl-6">
          <div className="absolute left-2 top-0 bottom-0 w-px bg-border" />
          <ul className="space-y-4">
            {timeline.map((t) => (
              <li key={t.year} className="relative">
                <span className="absolute -left-[7px] top-1.5 h-3 w-3 rounded-full bg-primary" />
                <div className="ml-2">
                  <div className="text-sm font-medium">{t.year}</div>
                  <div className="text-sm text-muted-foreground">{t.text}</div>
                </div>
              </li>
            ))}
          </ul>
        </div>
      </section>

      {/* CTA */}
      <section className="container mx-auto px-4 py-10">
        <Card className="overflow-hidden">
          <CardContent className="grid md:grid-cols-2 gap-6 p-6 md:p-10 items-center">
            <div>
              <h3 className="text-2xl font-semibold mb-2 flex items-center gap-2"><Calendar className="h-5 w-5"/> 협업/강의 문의</h3>
              <p className="text-sm text-muted-foreground mb-4">교육/워크숍, 커리큘럼 공동 개발, CSR 연계 프로젝트 등 제안 환영합니다.</p>
              <div className="flex flex-wrap gap-2">
                <Button asChild>
                  <a href="mailto:office@ppleedu.org">이메일 보내기</a>
                </Button>
                <Button asChild variant="outline">
                  <a href="https://cal.com/{{your-cal}}" target="_blank" rel="noreferrer">미팅 예약</a>
                </Button>
              </div>
            </div>
            <div className="rounded-xl ring-1 ring-border p-4 md:p-6 bg-muted/40">
              <p className="text-sm text-muted-foreground">
                최근 관심사: 느린학습자/다문화 대상 맞춤형 AI 창작 수업 확대, 지역 자원 기반 프로젝트(김포·전북 등),
                SSE 기반 채팅 성능 최적화, 프롬프트/스키마 관리 자동화.
              </p>
            </div>
          </CardContent>
        </Card>
      </section>

      {/* Footer */}
      <footer className="container mx-auto px-4 py-10 text-center text-sm text-muted-foreground">
        © {year} Hyukjun Bae · PPLE EDU · Made with ❤️
      </footer>
    </div>
  );
}
