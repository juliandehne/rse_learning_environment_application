# Prototype Fund application — Up and Coming track — DRAFT

**Call:** Prototype Fund, round 03, track *Up and Coming* · applications close
**30 November 2026, 15:00 CET** on <https://bewerben.prototypefund.de/>
**Rules:** [Application Guide 2026](https://www.prototypefund.de/uploads/Publikationen_und_Onepager/PTF_Application_Guide_2026.pdf)
**Funding period:** 1 June – 30 November 2027, optional Second Stage 1 December 2027 – 31 March 2028
**Working title:** *Lernknoten* / *RSE Learning Mesh* (placeholder — rename)
**Team:** Helene Skovlund Holst and Lukka Mayers (students), Julian Dehne (mentor)

Builds on the [RSE Learning Environment Hackathon](https://github.com/personalhel/RSE-hackathon)
(Glasgow, 26–27 Nov 2026) and on FL-Trail
([`gemeinsamforschen`](https://github.com/juliandehne/fltrail/tree/master/gemeinsamforschen),
[Dehne 2021](https://doi.org/10.25932/publishup-49789)). Question wording and word limits follow
the application questions and the Application Guide 2026. Answers may be in English; the formal
application to the ministry later must be in German.

---

## 0 · Check before submitting

| Rule (Application Guide 2026) | What it means for us | Status |
|---|---|---|
| Up and Coming: every funded person except the mentor is ≤ 25 on 1 June 2027 **or** enrolled in a degree / IT training programme on that date (proof required) | Helene and Lukka: confirm age or enrolment for June–Nov 2027 | **TODO** |
| Mentor may be over 25, need not be a student, must give practical support, **must be a GbR member**, and may take **at most 10 % of the total hours** | Julian ≤ 10 % — see hours in T6 | planned |
| Team ≤ 4, GbR seated in Germany; **at most one person abroad** (one third of a team of three) | Helene (Copenhagen) is the one person abroad → Lukka and Julian must live in Germany | **TODO confirm Lukka's residence** |
| Main contact = project lead, responsible for the formal application, **must be based in Germany** | Recommendation: **Lukka** as project lead (student-led track); Julian if Lukka is not in Germany | **decide** |
| Employment at a research institute related to the project must be declared (Q 1a.4/5) | Julian works at a university; no employer consent needed for the application itself — side-job notice (TV-L § 3 Abs. 4) to HR before June 2027 | **solved** |
| Open-source licence, public repository, ≤ 1,900 h for a team at max. €50/h, ≥ 5 % own contribution | Plan: 1,730 h ≈ €86,500 | planned |
| Topic focus of Innovation / Up and Coming: data security and **software infrastructure** | framed as research-and-teaching infrastructure (see P3/P4) | ok |

---

## General information

- Main contact / project lead: **TODO** (based in Germany — see 0)
- E-mail: **TODO** (a team address that is checked regularly)
- GitHub/GitLab of the main contact: **TODO**

## 1a · Eligibility

**1. Applying as a team?** Yes, three people.

**2. Applying with a mentor?** Yes: Julian Dehne, who designed and built the predecessor system
FL-Trail in his doctoral research and organises the RSE Learning Environment Hackathon.

**3. All applicants (except the mentor) are under 26 or enrolled in a degree / IT training?**
Yes — **TODO confirm per person**.

**4. Company shares, own organisation, or work for a related research institute?** Yes: the mentor
is employed at a university. **TODO:** check Helene and Lukka (student assistant jobs count if the
institute's remit is related).

**5. If so, why is the project not software for your own operations?** *(max. 100 words)*

The mentor's university neither commissions, owns nor operates the result. The software is an open,
institution-independent infrastructure component released under an open-source licence, designed
from the start for many universities, research centres and community courses — the hackathon that
seeds it brings together groups from Glasgow, Bonn, Copenhagen and Germany. No institution hosts
the project or depends on it for its own operations. The mentor contributes at most 10 % of the
hours, in his own time and with his employer's approval, and the development work is carried out
by the two student team members.

## Your project

### P1 · Describe your project in one sentence. *(max. 30 words)*

An open engine that runs project-based software-engineering courses across existing research
infrastructure — forges, JupyterHub, HPC clusters — so students practise teamwork, code review and
reproducible computing.

### P2 · Briefly describe your project. *(max. 100 words)*

Software engineering is learned by doing: in teams, on real repositories, with code review and on
the machines the code must run on. Learning platforms cannot offer this — they handle documents,
quizzes and grades, while the actual work happens on GitLab, in CI pipelines, in JupyterHub and on
HPC clusters. We build an open-source course engine that treats these systems as nodes of one
learning infrastructure: it forms teams, creates their repositories, collects submissions as
commits, assigns peer reviews, starts runs on the right compute and reports back to the university's
learning platform. Institutions keep their infrastructure and data.

### P3 · Which social issue do you want to address with the project? *(max. 175 words)*

Science increasingly runs on software. Climate projections, medical studies and social-science
analyses are only as trustworthy as the code behind them — and most of that code is written by
researchers who never learned to develop software in a team. Research software engineering (RSE)
has emerged to close this gap, but its training is fragmented and mostly read-only: lessons,
slides, static notebook sites.

The skills that make code trustworthy are practised, not read: working in a team, handing over a
runnable artefact, reviewing someone else's code, reproducing a result on another machine. Students
rarely get to practise them because the infrastructure is missing: universities run a learning
platform on one side and forges, clusters and notebook servers on the other, and nothing connects
them pedagogically. Teachers glue them together by hand or buy proprietary classroom products.

An open, self-hostable infrastructure layer lets every university — including small ones without an
RSE group — teach software engineering on real tools, keeps student data on public infrastructure
and makes good teaching reusable across disciplines and borders.

### P4 · How do you want to realize your project on a technical level? *(max. 175 words)*

A **process engine** plus **node adapters**, each a separate service with an open API.

The engine models a course as phases, tasks and constraints — the process model from FL-Trail,
reimplemented as a lightweight service (Python, **TODO confirm stack**). It decides *who works with
whom* (group formation by learning goals or complementary skills), *what is due when*, and *who
reviews whom* so that every team is guaranteed feedback.

Adapters connect the nodes a real course uses:

- **Forge** (GitLab, GitHub, Gitea/Forgejo): create team repositories, snapshot submissions at a
  commit, open review merge requests.
- **Compute**: run a submission in a container or JupyterHub; for HPC, submit to SLURM through Open
  OnDemand or a batch API, with per-course quotas.
- **Learning platform**: LTI 1.3 for launch and grade return to Moodle, ILIAS or Canvas.
- **Chat**: Matrix rooms per team.

Every node is optional and replaceable. Tests run against containerised GitLab, JupyterHub and a
small SLURM cluster. We license under MIT, as it is permissive. 

### P5 · Have you already worked on the idea? If so, briefly describe the current status and explain the planned new features. *(max. 100 words)*

Yes. FL-Trail, developed in the mentor's doctoral research at the University of Potsdam, supported
student research projects end to end: group formation via the GroupAL algorithm, submissions,
annotated feedback, peer assessment, reflection and a phase-based process engine. It was used in
courses, but it is a Java monolith from 2020 built around uploaded documents. In November 2026 the
RSE Learning Environment Hackathon in Glasgow gathers requirements from RSEs and educational
technologists **[after hackathon: add results]**. New: repositories instead of documents, adapters
to real infrastructure (forges, compute, HPC, learning platforms) instead of a closed platform, and
a modern, maintainable codebase.

### P6 · Link to the existing project

- FL-Trail: <https://github.com/juliandehne/fltrail/tree/master/gemeinsamforschen>
- GroupAL service: <https://github.com/juliandehne/groupal-mono>
- Hackathon: <https://github.com/personalhel/RSE-hackathon>
- This application: <https://github.com/juliandehne/rse_learning_environment_application>

### P7 · What is innovative about your project? If there are similar projects, how does your approach go beyond them, and why can't you build on them? *(max. 100 words)*

Existing tools each cover one node. Learning platforms (Moodle, ILIAS) manage documents and grades
but not repositories or compute. GitHub Classroom creates repositories but is proprietary, bound to
one commercial forge and has no pedagogical group formation or review assignment. RSE training
platforms such as Oxford's open-source Gutenberg deliver courses and track progress, but learners
never form teams, run code on real infrastructure or review each other. Our approach is new in
treating the learning environment as a *federation of existing infrastructure*, orchestrated by a
validated pedagogical process model. We reuse these tools as nodes rather than replacing them.

### P8 · Who are the potential users of your project and how do you want to reach them? *(max. 100 words)*

Teachers of project-based software-engineering and RSE courses, and their students — computer
science students as well as doctoral researchers in other sciences who write research code. We
reach them through concrete pilots: **TODO — name at least two courses in winter term 2027/28**
(candidates from the hackathon network: University of Glasgow, iBOTS Bonn, University of
Copenhagen, the mentor's own courses). The hackathon participants are our first testers from June
2027. We contribute adapters upstream where tools are open (e.g. Gutenberg) and publish
ready-to-run deployment recipes, so that a teacher can start a course without an RSE group.

### P9 · Briefly outline the most important milestones that are to be implemented during the funding period. *(max. 100 words)*

- **June:** architecture and API contract; process engine with group formation and phase model
  (port from FL-Trail), containerised test environment.
- **July–August:** forge adapter (GitLab, GitHub): team repositories, submission at a commit, review
  assignment as merge requests.
- **September:** compute adapter (containers, JupyterHub) and LTI 1.3 link to Moodle/ILIAS;
  proof-of-concept SLURM adapter on a test cluster.
- **October–November:** pilot in at least two real courses, fixes from teacher and student feedback,
  documentation and deployment recipes, Demo Day.

## Team and experience

### T1 · Team members, role and weekly hours *(max. 30 words)*

Helene Skovlund Holst — frontend, LTI and teaching integration, 30 h/week. Lukka Mayers — process
engine and infrastructure adapters, 30 h/week. Julian Dehne — mentor, ~6.5 h/week.
*(TODO: swap roles if needed — names are binding)*

### T2 · Which software projects have you worked on so far? *(max. 100 words)*

**TODO — per person with repository links.**
Helene: RSE hackathon website (Quarto, GitHub Pages) — <https://github.com/personalhel/RSE-hackathon>; […].
Lukka: […].
Julian (mentor): FL-Trail (<https://github.com/juliandehne/fltrail>), GroupAL service
(<https://github.com/juliandehne/groupal-mono>), competence database
(<https://github.com/juliandehne/competence-database>); […].

### T3 · Total hours in the 6-month period

**1,730 h** (≈ €86,500 at €50/h; cap 1,900 h):
Helene 780 h (30 h × 26 weeks), Lukka 780 h, Julian 170 h (6.5 h × 26 weeks = 9.8 % — below the
10 % mentor cap).

### T4 · Experience, background, motivation, perspective: what should the jury know? *(max. 100 words)*

**TODO — sharpen with Helene and Lukka; first person plural, student voice.**
We are students who learned software engineering the hard way — on tools our courses never showed
us. Helene studies at the University of Copenhagen and co-organised the RSE Learning Environment
Hackathon; Lukka […]. Our mentor Julian Dehne researched software support for group-based learning
in his doctorate and built FL-Trail, its predecessor; he guides architecture and pedagogy, we build.
Through the hackathon, RSE groups and educational technologists in the UK, Germany and Denmark want
to use the result in their teaching — so we build with first users, not for hypothetical ones.

## Second Stage

### S1 · Do you apply for the four-month Second Stage?

Yes (**TODO confirm**). Cap for a team: ≈ 1,267 h.

### S2 · What does your project need to move beyond the prototype stage, and how will you build it sustainably in four months? *(max. 175 words)*

After the pilots the engine works in a few courses run by people who helped design it. To become
infrastructure others rely on, it needs three things.

**Real HPC.** The SLURM adapter is a proof of concept on a test cluster. Teaching on a production
cluster requires federated login, project allocations and fair-use quotas; we will harden the
adapter with one university computing centre **(TODO: partner)** and document what other centres
need to offer it.

**Assessment that teachers trust.** Peer review exists; turning learner and teacher judgements into
a grade needs a transparent co-assessment procedure with explicit weighting, which FL-Trail
prototyped and the pilots will ask for.

**Maintainership and adoption.** A 1.0 release with a security policy, a second maintainer outside
the team, an instructor guide with a hosted demo course, and onboarding of three further courses,
at least one outside the hackathon network.

Wherever new features and hardening conflict, hardening wins.

### S3 · Milestones for the four-month extension *(max. 100 words — check)*

- **December–January:** SLURM/Open OnDemand adapter on a production cluster with a computing-centre
  partner; release 1.0.
- **February:** co-assessment module; second maintainer onboarded.
- **March:** three further courses onboarded; instructor guide and demo course; maintenance plan
  after funding.
