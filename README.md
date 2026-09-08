# SU(3) 格点规范理论的顶点多重性量子比特编码 (su3-vertex-encoding)

## 1. 我们要解决的核心问题

在利用量子计算模拟量子色动力学（QCD / SU(3) 非阿贝尔规范场）的实时动力学时，体系必须严格满足**局域高斯定律**：格点上每个顶点（vertex）与其相连的 4 条连边（links），其色荷直积必须构成一个**平凡单态（Color Singlet / 规范不变态）**。

- **SU(2) 的天然优势**：在 SU(2) 规范群中，角动量耦合系数（Clebsch-Gordan 系数）没有多重性。一旦连边的不可约表示与中间虚态确定，顶点的单态基底是唯一的。
- **SU(3) 的内在挑战（多重性 Multiplicity）**：在 SU(3) 中，不可约表示的直积存在内在多重性（例如最低阶的胶子伴随表示 $\mathbf{8} \otimes \mathbf{8} = \mathbf{1} \oplus \mathbf{8}_S \oplus \mathbf{8}_A \oplus \mathbf{10} \oplus \overline{\mathbf{10}} \oplus \mathbf{27}$，其中伴随表示 $\mathbf{8}$ 出现了**两次**）。当 4 条连边汇聚在一个顶点时，形成单态的基底态不再唯一，存在多个简并分支（例如 $\dim \mathrm{Inv}(\mathbf{8}^{\otimes 4}) = 8$）。
- **现有工作的妥协与缺口**：现有前沿工作（如 Ciavarella et al., arXiv:2608.28752 附录 A）为了强行把局域构型压到一个量子比特上，**暴力截断掉了需要多重跃迁的态**。这在强耦合和长时间演化下会导致物理保真度严重失真。
- **本项目核心目标**：**设计并实现一种既不丢失多重性信息、又严格保持局域性与规范不变性的 SU(3) 顶点多重性量子比特编码方案**。

---

## 2. 核心衡量标准

1. **量子比特开销 (Qubit Count)**：每个顶点/每个 plaquette 所需量子比特数随截断表示维度 $\Lambda$ 的增长率。
2. **算符局域性与 Pauli 项数**：磁场项 $\mathrm{Tr}(U_\square)$ 在量子比特基底下展开的 Pauli 权重与项数。
3. **动力学保真度**：对比暴力截断方案与本方案在实时演化（如弦断裂、胶子震荡）中的物理精度。

---

## 3. 开发环境说明

- 专属虚拟环境路径：`su3_env/`
- 激活环境命令（Windows PowerShell）：
  ```powershell
  .\su3_env\Scripts\Activate.ps1
  ```
- 运行依赖安装：
  ```powershell
  pip install -r requirements.txt
  ```
