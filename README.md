graph TD
    A[开始训练过程] -->|步骤 1 | B(SurfaceCostNet 预训练)
    B --> C{生成概率图 P}
    C --> D[高斯分布 ˆPq]
    D --> E[结束 SurfaceCostNet 预训练]

    E --> F[SurfaceShapeNet 训练]
    F --> G[使用 Sgt 生成 地面真实 ˆd]
    G --> H[计算 Lossshape]
    H --> I[平滑 ˆd 进行训练]
    
    I --> J[微调阶段]
    J --> K[使用 L1 损失]
    K --> L[交替训练 SurfaceCostNet & OSInet]
    L --> M[使用训练/验证数据]

    M --> N[性能评估]
    N --> O[分割精度评估]
    N --> P[标注数据需求评估]
    N --> Q[对抗性噪声鲁棒性评估]
    
    O --> R[评估完成]
    P --> R
    Q --> R
    
    R --> S[结束]
