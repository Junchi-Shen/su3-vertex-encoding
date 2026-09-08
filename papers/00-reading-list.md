# SU(3) 格点规范理论量子模拟：入门阅读清单

整理日期：2026-09-07。按你的四个短板分层：哈密顿量格点规范理论、SU(3) 表示论、规范不变子空间与顶点多重性、哈密顿量模拟误差理论。所有链接已核对。

标记说明：★ 必读；○ 可选。

---

## 第 0 层：先铺地图（两三天）

- ★ Davoudi, *TASI/CERN/KITP Lecture Notes on "Toward Quantum Computing Gauge Theories of Nature"* (2025), 58 页, 7 道习题。
  https://arxiv.org/abs/2507.15840
  这个领域目前唯一一份系统讲义。Kogut–Susskind 哈密顿量、希尔伯特空间与物理态、初等数值方法、电路设计与资源估计、U(1) 逐步示例、QCD 代价概览。作为主线教材，其它材料都挂在它上面。
- ★ Preskill, *Simulating quantum field theory with a quantum computer* (Lattice 2018 大会报告)。
  https://arxiv.org/abs/1811.10085
  短，讲清"为什么要用量子计算机做 QFT"和符号问题。周末一晚读完。
- ○ Bauer, Davoudi, Klco, Savage, *Quantum simulation of fundamental particles and forces*, Nat. Rev. Phys. 5, 420 (2023)。
  https://arxiv.org/abs/2404.06298
  12 页全景，核物理与高能物理两边的机会和难点。面试前复习用。

## 第 1 层：哈密顿量格点规范理论（短板一）

- ★ Kogut & Susskind, *Hamiltonian formulation of Wilson's lattice gauge theories*, Phys. Rev. D 11, 395 (1975)。
  https://doi.org/10.1103/PhysRevD.11.395
  原始论文，出人意料地好读。刚体转子图像、电通量弦、强耦合极限下的禁闭。
- ★ Kogut, *An introduction to lattice gauge theory and spin systems*, Rev. Mod. Phys. 51, 659 (1979)。
  https://doi.org/10.1103/RevModPhys.51.659
  经典教学综述。只读哈密顿量格点规范理论与转移矩阵的章节，Ising 对偶部分可跳。UW 校内网可下载。
- ★ Zohar & Burrello, *Formulation of lattice gauge theories for quantum simulations*, Phys. Rev. D 91, 054506 (2015)。
  https://arxiv.org/abs/1409.3085
  用量子模拟界的语言重写 Kogut–Susskind：链接希尔伯特空间的表示基 |j m m'⟩、左右生成元、高斯定律的算符形式。你项目用的电场基就是这一套。
- ★ Zohar, *Quantum simulation of lattice gauge theories in more than one space dimension*, Phil. Trans. R. Soc. A 380, 20210069 (2022)。
  https://arxiv.org/abs/2106.04609
  专讲 d ≥ 2 为什么难：方格项、非阿贝尔高斯定律、顶点希尔伯特空间。直接对应你的论文设定。
- ○ Tong, *Gauge Theory* 讲义（剑桥，免费），格点规范理论一章。
  https://www.damtp.cam.ac.uk/user/tong/gaugetheory.html
  补连续场论到格点的过渡：Wilson 圈、禁闭、连续极限。
- ○ Gattringer & Lang, *Quantum Chromodynamics on the Lattice*, Springer LNP 788 (2010)。
  https://link.springer.com/book/10.1007/978-3-642-01850-3
  欧氏路径积分那一侧的标准教材。只需第 2、3 章：链接变量、方格、规范不变性。
- ○ 中文：刘川《格点量子色动力学导论》（北京大学出版社 2017）；冯旭《格点量子色动力学基础》讲义（2018 上海交大暑期学校，免费 PDF）。
  https://indico.ihep.ac.cn/event/11211/contributions/8428/attachments/4080/4641/lattice_feng_xu.pdf
  两者都是欧氏路径积分体系，用来补格点语言的中文直觉，不覆盖哈密顿量形式。

## 第 2 层：SU(3) 表示论（短板二）

- ★ Georgi, *Lie Algebras in Particle Physics*, 2nd ed.（开放获取 PDF）。
  https://library.oapen.org/bitstream/20.500.12657/50876/1/9780429967764.pdf
  读 SU(3)、张量方法、杨图三章。8 ⊗ 8 = 1 ⊕ 8 ⊕ 8 ⊕ 10 ⊕ 10̄ ⊕ 27 这一行的来历就在这里。
- ★ Alex, Kalus, Huckleberry, von Delft, *A numerical algorithm for the explicit calculation of SU(N) and SL(N,C) Clebsch–Gordan coefficients*, J. Math. Phys. 52, 023507 (2011)。
  https://arxiv.org/abs/1009.0437
  基于 Gelfand–Tsetlin 模式的数值 CG 算法，附录带代码，只假设你会 SU(2)。外多重性被显式处理。这是你第 1 周验算代码的直接蓝本。
- ○ Greiner & Müller, *Quantum Mechanics: Symmetries*, Springer。
  https://link.springer.com/book/10.1007/978-3-642-57976-9
  SU(3) 一章手算 CG 系数，例题多，适合动笔。
- ○ 中文：马中骐《物理学中的群论》（科学出版社，第三版 2015），SU(N) 群一章。
  https://book.douban.com/subject/26673926/

## 第 3 层：规范不变子空间与顶点多重性（短板三，也是你论文的直接前置文献）

按顺序读，先 SU(2) 再 SU(3)。

- ★ Raychowdhury & Stryker, *Loop, string, and hadron dynamics in SU(2) Hamiltonian lattice gauge theories*, Phys. Rev. D 101, 114502 (2020)。
  https://arxiv.org/abs/1912.06133
  SU(2) 没有多重性，机制看得最干净。先在这里理解"显式规范不变的局域基"怎么搭。
- ★ Davoudi, Raychowdhury, Shaw, *Search for efficient formulations for Hamiltonian simulation of non-Abelian lattice gauge theories*, Phys. Rev. D 104, 074505 (2021)。
  https://arxiv.org/abs/2009.11802
  横向比较 Kogut–Susskind、LSH、量子链接等形式在截断后的代价。写论文相关工作一节时的骨架。
- ★ Anishetty, Mathur, Raychowdhury, *Prepotential formulation of SU(3) lattice gauge theory*, J. Phys. A 43, 035403 (2010)。
  https://arxiv.org/abs/0909.2394
  用 Schwinger 玻色子加 Sp(2,R) 约束处理 SU(3) 顶点多重性的经典做法。配套读 Raychowdhury 的博士论文（Bose Institute，免费 PDF），讲得更慢：
  https://www.bose.res.in/linked-objects/academic-programmes/PhD%20Thesies/2013/Indrakshi%20Raychowdhury_thesis.pdf
- ★ Kadam, Naskar, Raychowdhury, Stryker, *Loop-string-hadron approach to SU(3) lattice Yang-Mills theory: I. Hilbert space of a trivalent vertex*, Phys. Rev. D 111, 074516 (2025)。
  https://arxiv.org/abs/2407.19181
  直接讨论 SU(3) 顶点的"缺失标签 / 外多重性"问题、非正交基与第七个 Casimir 算符。与你的项目最接近的已有工作，必须读并引用。续篇 II（算符表示）：https://arxiv.org/abs/2512.11796
- ○ Ciavarella, Klco, Savage, *Trailhead for quantum simulation of SU(3) Yang-Mills lattice gauge theory in the local multiplet basis* (2021)。
  https://arxiv.org/abs/2101.10227
  上次清单已有，这里只提醒：它对 d ≥ 2 顶点多重性的处理方式是你论文要对比的基线之一。

## 第 4 层：哈密顿量模拟算法与误差（短板四）

- ★ Childs, *Lecture Notes on Quantum Algorithms*（UMD，免费 PDF），哈密顿量模拟一章。
  https://www.cs.umd.edu/~amchilds/qa/qa.pdf
- ★ Childs, Su, Tran, Wiebe, Zhu, *Theory of Trotter error with commutator scaling*, Phys. Rev. X 11, 011020 (2021)。
  https://arxiv.org/abs/1912.08854
  读引言和一阶、二阶公式部分即可。对易子范数界正是你应用数学功底最容易发力的地方。

## 第 5 层：hello world 与经典基线

- ★ Martinez 等, *Real-time dynamics of lattice gauge theories with a few-qubit quantum computer*, Nature 534, 516 (2016)。
  https://arxiv.org/abs/1605.04570
  第一次实验，4 个离子比特跑 Schwinger 模型。
- ★ Klco 等, *Quantum-classical computation of Schwinger model dynamics using quantum computers*, Phys. Rev. A 98, 032331 (2018)。
  https://arxiv.org/abs/1803.03326
  两格点 Schwinger 模型上 IBM 机器。演示如何用对称性把希尔伯特空间砍掉五倍。对应你计划里的第 1 步。
- ○ Pinto Barros, Fontana, Sodano, Trombettoni, *The lattice Schwinger model and its quantum simulation* (2025)，12 页。
  https://arxiv.org/abs/2512.11533
- ○ Cataldi 博士论文, *Hamiltonian lattice gauge theories: emergent properties from tensor network methods* (2025)，150 页。
  https://arxiv.org/abs/2501.11115
  张量网络做哈密顿量格点规范理论的经典基线，dressed-site 截断在 2D SU(2) 上的实现。对你的 phase0-mps 目录直接有用，挑章节读。
- ○ Klco 博士论文 (UW 2020), *Calculating Nature Naturally: Toward Quantum Simulation of Quantum Fields*。
  https://digital.lib.washington.edu/researchworks/handle/1773/46546
  IQuS 出品，UW 图书馆免费 PDF。
- ○ Klco, Roggero, Savage, *Standard model physics and the digital quantum revolution*, Rep. Prog. Phys. 85, 064301 (2022)。
  https://arxiv.org/abs/2107.04769
  长综述，当索引用。
- ○ Halimeh 等, *Cold-atom quantum simulators of gauge theories*, Nat. Phys. 21, 25 (2025)。
  https://arxiv.org/abs/2310.12201
  模拟型平台那一侧，了解即可。

---

## 建议顺序（四周）

| 周 | 读 | 做 |
|---|---|---|
| 1 | Davoudi 讲义前三章；Preskill；Georgi SU(3) 三章 | 用 Alex 等的算法写 SU(3) 张量积分解代码，验算 8⊗8 |
| 2 | Zohar & Burrello；Kogut 1979 哈密顿量章节；Zohar 2022 | 手推单个顶点的高斯定律与物理态 |
| 3 | LSH SU(2) → 预势 SU(3) → Kadam 2025 I、II | 写论文相关工作一节草稿 |
| 4 | Childs 讲义；Trotter 误差论文；Martinez；Klco 2018 | Qiskit 跑通 Schwinger 模型，与精确对角化对比 |

## 一个需要修的地方

项目 README 把 arXiv:2608.28752 当作"暴力截断 SU(3) 多重态"的现有工作来引用。核对后该文是 Ciavarella, de Putter, Younis, Rrapaj (2026-08-28) 的 *Quantum Simulations of Two-Dimensional Non-Abelian Adjoint String Breaking*，做的是三角格子上的纯 SU(2) 理论，用局域 Krylov 截断。SU(2) 没有外多重性，所以它不能作为 SU(3) 多重性被截掉的例证。对应 SU(3) 的基线应改引 Kadam 等 2025 和 Ciavarella–Klco–Savage 2021。
