# こんにちは、pitchipt-dotcomです 👋

理学療法士として臨床で働きながら、現場や家庭で実際に困ったことをソフトウェアで解決する個人開発を続けています。AIを使うこと自体を目的にせず、役立つ道具にできるかを試し、確かめ、必要な形へ育てることを大切にしています。

## 開発テーマ

- **AIシステム開発**：Python、ローカルLLM、RAG、MCP、AIエージェント、API連携、業務自動化
- **ローカル実行**：自宅Linux PC（RTX 3060 12GB / RAM 64GB）を使い、モデルやデータを手元で扱う構成を開発
- **現場の課題を道具にする**：臨床教育、情報整理、家族で使う学習アプリなど、利用場面から設計
- **段階的な自動化**：Solve → Toolify → Agentify。まず仕事を解き、確かめられる手順を道具にし、その後で判断が必要な箇所にAIを組み込む

## 代表プロジェクト

### 1. ローカルAI統合環境 — [Pitchi-chat](https://github.com/pitchipt-dotcom/pitchi-chat)

自宅Linux環境で動かす、スマートフォン対応のAI統合Webアプリです。ローカルLLMとの会話、画像・動画・音声生成のHost連携、履歴・成果物管理をまとめています。

- **技術**：Python、FastAPI、JavaScript、ローカルLLM API、ComfyUI、SQLite
- **課題と工夫**：複数のAIサービスをスマートフォンから扱いやすくし、重量級モデルをオンデマンドで起動・共有する。生成ジョブ、リソース利用、成果物をHost側で管理する
- **状況**：Public。各生成機能は対応するモデル・サービスの別途導入が必要です。長尺動画の上限構成はありますが、180秒の連続生成品質は未検証です

![Pitchi-chatのスマートフォン画面](assets/pitchi-chat-mobile.png)

### 2. AIエージェント・業務自動化 — [Pitchi-work](https://github.com/pitchipt-dotcom/pitchi-work)

LLMの提案をそのまま実行結果にせず、Hostが仕事の範囲、工程、証拠、検証、承認を管理するPython製のエージェント基盤です。

- **技術**：Python、CLI、ローカルLLM API、各種コマンド・API連携
- **課題と工夫**：LLMの文章上の「完了」を成功と誤認しないよう、Host validator、隔離実行、source pin、root acceptance、承認を使って成果物を確認する
- **開発方針**：Solve → Toolify → Agentify。決定的なCLIや検証を優先し、言語理解が必要な部分にLLMを使う
- **状況**：Public。登録済みの作業範囲とvalidatorを中心に使う仕組みで、任意の仕事を自律的に完遂する汎用システムではありません

### 3. 理学療法・臨床教育 — [Pitchi-PT Simulator](https://github.com/pitchipt-dotcom/PitchiPT-simulator)

教科書の知識をベッドサイドの判断へつなぐための臨床ケース学習アプリです。症例を読み、評価・判断・介入を順に考えるシミュレーションを提供します。

- **技術**：React、Vite、JavaScript。Vercelで公開
- **PWAについて**：現在の公開ブランチにはWeb App ManifestとService Workerが見当たらないため、この紹介ではVercel公開のReact/Viteアプリとして記載しています。
- **課題と工夫**：疾患知識だけでなく、リスク管理や目標設定など、臨床で何を優先するかを考える練習をケース形式にする
- **状況**：Public、Webで利用可能。教育用のケース教材であり、実患者への診断・治療指示ではありません

[公開アプリを開く](https://pitchi-pt-simulator.vercel.app)

### 4. 子どもの学習支援 — [けいさんプリンセス](https://github.com/pitchipt-dotcom/keisan-princess)

子どもが遊びながら計算を練習できるReactアプリです。九九、くり上がりのある足し算、くり下がりのある引き算、10づくりと、キャラクターの着せ替え・コレクションを組み合わせています。

- **技術**：React 18、Vite、JavaScript、Web App Manifest、Service Worker、localStorage。Vercelで公開
- **Androidでの利用**：PWAとしてホーム画面に追加して利用できます。リポジトリにAPK/AABを生成するAndroidネイティブパッケージ工程はありません
- **課題と工夫**：計算練習を続けやすくするため、問題に取り組んでアイテムを集める遊びを加える。進捗は端末のブラウザに保存し、バックアップコードで移行できます
- **状況**：Public、Webで利用可能。端末のブラウザデータを消すと進捗も消えるため、アプリ内のバックアップ機能を利用してください

![けいさんプリンセスのスマートフォン画面](assets/keisan-princess-mobile.png)

[公開アプリを開く](https://keisan-princess.vercel.app)

## 技術の広がり

| 領域 | 取り組み |
|---|---|
| Python / AIバックエンド | FastAPI Host、ローカルLLM接続、API連携、ジョブと成果物管理 |
| LLM / エージェント | 推論の役割分担、有限ワークフロー、Hostによる検証・承認 |
| 生成メディア | ComfyUI画像生成、動画・音声サービスとのadapter連携 |
| Web / PWA | React、Vite、スマートフォン向けUI、localStorage、Service Worker |
| 自動化 | CLIを使った決定的処理、テスト、隔離実行、手順の再利用 |

## 進め方

1. **Solve** — 実際の課題と成功条件を明確にし、まず人が確認できる方法で解く。
2. **Toolify** — 繰り返せる手順をCLI・APIやテストにする。
3. **Agentify** — 必要な判断にLLMを使い、Hostが入力範囲・実行・検証・承認を管理する。

AIの出力だけで成功を決めず、可能な範囲でテスト、原典、CLI、Host側の検証につなげます。

## Links

- [GitHub repositories](https://github.com/pitchipt-dotcom?tab=repositories)
- [Pitchi-chat](https://github.com/pitchipt-dotcom/pitchi-chat) · [Pitchi-work](https://github.com/pitchipt-dotcom/pitchi-work)
- [Pitchi-PT Simulator](https://github.com/pitchipt-dotcom/PitchiPT-simulator) · [けいさんプリンセス](https://github.com/pitchipt-dotcom/keisan-princess)

---

理学療法の現場と家庭で見つけた小さな不便を、使う人に合わせたソフトウェアへ変えていくことが開発の軸です。
