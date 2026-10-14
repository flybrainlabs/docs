# 构建与贡献

在所属组件仓库编辑，使用组装工作区构建。组装器只提供构建布局，不是另一个源码所有者。新文件必须登记到适用的 `component.json` 映射。

## 前提

使用 Rust **1.90 或更新版本**、Node **22 或更新版本**、Python **3.11 或更新版本**。浏览器工具采用固定 npm 依赖。WebAssembly 需要 wasm32 target，SBF 需要兼容的 Solana/Agave 工具。科学准备和完整模型检查还需要可选依赖与真实输入资源。

手册生成器使用 `tools/requirements-docs.txt` 固定 Python 依赖。生成 HTML 随源码提交，因此阅读或提供发布版本不需要运行时 Markdown 渲染。

## 认证检出固定版本

```sh
git clone https://github.com/flybrainlabs/infra.git flybrainlabs/infra
python3 flybrainlabs/infra/tools/workspace.py checkout \
  --repos flybrainlabs --transport ssh
python3 flybrainlabs/infra/tools/workspace.py assemble \
  --repos flybrainlabs --output flybrainlabs-workspace
cd flybrainlabs-workspace
npm ci
```

在仓库外配置获准 GitHub SSH 身份，不要将令牌写进 URL。必须有私有 web 仓库访问权。包含清单的 infra 修订固定组装器自身，清单固定其余组件。

## 基本构建与相关检查

```sh
npm run build:web
cargo check --locked --bin flypow-web
python3 -B -m unittest discover -s tests -p test_static_export.py -v
```

数值 WebAssembly 核心：

```sh
rustup target add wasm32-unknown-unknown
cargo build --locked --release -p flypow-sim-core \
  --target wasm32-unknown-unknown
```

历史可执行文件和包名称是保留的兼容标识，构建它们不会恢复旧品牌。

## 编辑与验证

编辑所属仓库并登记新文件，再明确使用 `--working-tree` 组装。该模式验证本地修改，不声称是固定发布。若有意在组装中编辑，`workspace.py sync` 检查并发后同步回所属仓库，请审阅差异。

运行与实际修改相关的检查。完整模型测试使用已验证资源并需要明确参数。不要为静态或文档测试清空模型、浏览器配置。大型导出需磁盘支持的临时空间。

官网手册维护英文 `docs/handbook/` 和中文 `docs/handbook/zh/`，运行 `tools/build_documentation.py`，检查链接与图例并执行一致性检查。来源和生成契约见[文档维护](https://github.com/flybrainlabs/docs/blob/main/docs/DOCUMENTATION_CENTER.md)。

## 英文维护与发布

技术维护文档、注释、提交和发布说明使用英文。官网产品界面与阅读手册支持中英文。历史摘要内容即使含其他语言也保持原始字节。

验证后扫描暂存文件和历史，检查获准远端变更，再以普通快进提交推送。将 infra 依赖固定到已核实组件提交，并推送包含清单的提交。不强推、不合并旧草案 PR、不发布到弃用账户。

密钥、钱包文件、会话令牌、节点数据库、私有成果、浏览器配置与模型缓存保留在 Git 和公开发布之外。仓库发布不激活生产资金。
