# CursorとAIコーディング入門

## 1. Cursorとは

Cursorは、AIを活用した次世代のコードエディタです。Visual Studio Codeをベースにしながら、AIによるコード補完、説明生成、リファクタリング支援などの機能を提供します。(2025/05/09現在, 学生はProプランを無料で使用できる?)

**主な特徴:**
- **多数のモデルを使用できる**
- AIによる高度なコード補完
- 自然言語でのコード生成
- コードの説明生成
- バグの検出と修正提案
- リファクタリング支援
- マルチ言語対応

**Juliaでの特徴的な機能:**
Juliaのコードを書く際、Cursorは数値計算に特化した文脈でコードを生成してくれる印象があります。モジュールの扱いもうまく理解し、適切な提案をしてくれるため、科学技術計算・シミュレーションコードの開発において非常に便利です。

## 2. インストールと基本設定

### 2.1 インストール方法
1. [Cursor公式サイト](https://cursor.sh/)からダウンロード
2. インストーラーを実行
3. 初回起動時の設定を完了

## 3. AIとの効果的な対話

AIとの対話を効果的に行うことで、開発効率を大幅に向上させることができます。Cursorは、ユーザーが入力したコード、開いているファイル、カーソル位置、対話履歴、およびカスタムルールをコンテキストとしてAIに提供します。さらに、必要に応じてコードベース全体やウェブを検索するツールも使用できます。このコンテキストと機能を意識して質問することが重要です。

### 3.1 AIへの質問方法

AIとの対話は、チャットパネル、インラインチャット、編集操作など様々な方法で行えますが、効果的な質問の原則は共通です。以下の点を意識することで、AIからより質の高い回答やコード生成を引き出すことができます。

**Cursorは, チャット内で「@」でフォルダやファイルを簡単に指定することができます。** さらに, 後で説明される「カスタムルール」を使用することで, よりAIの応答が洗練されます。

1.  **目的を明確に伝える**: 何を知りたいのか、何を達成したいのかを具体的に伝えます。
    *   **コードに関する質問**: 「この関数のバグを修正したい」「この機能を追加するコードを生成して」
    *   **知識に関する質問**: 「Juliaのマルチスレッディングについて教えて」「文化進化シミュレーションでよく使われるモデルは？」(情報が古い場合があるので、最新の情報を確認すること。もしくは, 参照させること。)
    *   **コードベース探索**: 「エージェントの初期化に関連するコードはどこにある？」「データの保存方法について書かれた箇所を教えて」

2.  **利用可能な情報を提示する**: AIが回答を生成するために役立つ情報を提供します。開いているファイルや選択範囲は自動的にコンテキストとして共有されますが、それ以外の情報が必要な場合は明示的に伝えます。コードベース全体の情報が必要だが場所が分からない場合は、探してほしい内容を具体的に記述します。
    *   **例**: 「このエラーメッセージが出る原因を調べたい（エラーメッセージを貼り付け）」「このライブラリ（`Agents.jl` など）の使い方を知りたい」
    *   **コードベース探索のヒント**: 探したい機能、関連するキーワード、ファイルの種類（例: `.jl` ファイル、`.md` ファイル）など、覚えている限りの情報を提供します。

3.  **必要な出力形式を指定する**: コード、説明、箇条書き、ステップ形式など、どのような形式で回答が欲しいかを指定します。特にコードベース探索や知識に関する質問では、求めている情報の種類を明確にすると良いでしょう。
    *   **例**: 「このトピックについて、初心者にも分かるように概要を説明してください」「関連する関数とその簡単な説明をリスト形式で出力してください」「この概念のJuliaでの実装例を見せてください」

4.  **制約や条件を明確にする**: 回答に含めるべき、あるいは除外すべき制約や条件があれば指定します。カスタムルールもここで考慮されます。
    *   **例**: 「Julia 1.7以降の機能に限定して説明してください」「このプロジェクトのコーディング規約（カスタムルールで設定済み）に従ってコードを生成してください」「公式ドキュメントの情報源を優先してください」

5.  **対話を通じて refine する**: 初回の回答が期待通りでなくても、追加の情報提供や具体的なフィードバックを通じて、対話を繰り返すことでより適切な回答やコードに近づけることができます。
    *   「ありがとう、ただ、もう少し具体的なコード例が欲しいです」「この説明のこの部分がよく分かりません。別の言葉で説明してもらえますか？」

**特に、知識に関する質問やコードベース探索を行う場合は、以下の点を加えると効果的です:**
- **具体的かつ簡潔に**: 何を知りたいか、何をどこで探してほしいかを具体的に、しかし簡潔に記述します。
- **キーワードを活用**: 関連しそうな単語やフレーズを含めると、AIが適切な情報を見つけやすくなります。
- **目的を伝える**: なぜその情報が必要なのか（例: 「〇〇というバグの原因を特定したい」「△△という新しい機能を実装するために参考にしたい」）を伝えると、AIはより目的に沿った回答を提供しやすくなります。

### 3.2 カスタムルールの活用

カスタムルールは、AIとの対話をより効率的かつ一貫性のあるものにするための重要な機能です。プロジェクト固有のルールやコーディング規約をAIに伝えることで、より的確なコード生成や提案を得ることができます。こちらも参考にされたし > https://github.com/kinopeee/cursorrules

#### 3.2.1 カスタムルールの設定方法

カスタムルールは `.cursor/rules` ディレクトリ内に `.mdc` 拡張子のファイルとして作成します。Cursorの設定画面からもGUIで作成・編集が可能です。

1. プロジェクトのルートディレクトリに `.cursor/rules` ディレクトリが存在するか確認（なければ作成）
2. `.cursor/rules` ディレクトリ内に、ルール内容を記述した `.mdc` ファイルを作成（例: `my_project_rules.mdc`）
3. `.mdc` ファイル内でルールの内容を記述し、適用方法（ルールタイプ）を指定

**基本的なディレクトリ構造:**
```
プロジェクトルート/
├── .cursor/
│   ├── rules/
│   │   ├── general_coding_style.mdc
│   │   ├── project_specific_rules.mdc
│   │   └── ...
```

#### 3.2.2 ルールタイプ

`.mdc` ファイルの先頭で `@rule_type:` という形式で、そのルールをAIが参照する頻度や状況を指定します。主なルールタイプは以下の通りです。

- `@rule_type: Always`: 常にAIが参照するべきルール。プロジェクトの根幹に関わる規約などに適しています。
- `@rule_type: Auto Attached`: 特定の条件（例: ファイルタイプ、ディレクトリ）に基づいて自動的に参照されるルール。Cursorの設定で詳細な条件を設定できます。
- `@rule_type: Agent Requested`: AIがユーザーに確認を求めた上で参照するルール。
- `@rule_type: Manual`: ユーザーが明示的に参照を指示した場合のみ参照されるルール。

効果的なカスタムルールの活用には、適切なルールタイプを選択することが重要です。

#### 3.2.3 カスタムルールの内容

ルールファイル (.mdc) には、AIに守ってほしいルールや参照してほしい情報を記述します。Markdown形式で記述でき、人間にとっても読みやすい形式で管理できます。

記述する内容の例:

1. **コーディングスタイルと規約:**
   - 変数名、関数名、型名などの命名規則
   - インデント、スペース、改行などの書式
   - コメントやドキュメンテーションの書き方
   - コードの構造やファイル分割の基準

2. **プロジェクト固有の情報:**
   - プロジェクトの目的と概要
   - 使用している主要なライブラリやフレームワーク、そのバージョン
   - 特定のアルゴリズムやデータ構造に関する詳細
   - アーキテクチャ上の制約や設計思想

3. **参照すべき重要ファイル:**
   - AIに常に意識してほしいファイルの内容
   - これらのファイルの内容を `.mdc` ファイル内に含めるか、参照方法を指示します。

特に現状では、AIが読み込むファイルを間違えたり、指示内容を誤認識したりすることがあります (もちろん, 人間が丁寧に指示を行えばいいのですが, それでは効率が悪いです)。これを防ぐためには、例えば以下のようなプロジェクト情報をファイルにまとめ、カスタムルールで参照させるのが効果的です。
*   プロジェクトの進捗: [`project_info/progress.md`](../../.cursor/context/project_info/progress.md)
*   ディレクトリ構成: [`project_info/directorystructure.md`](../../.cursor/context/project_info/directorystructure.md)
*   技術スタック（使用ライブラリやバージョンなど）: [`project_info/technologystack.md`](../../.cursor/context/project_info/technologystack.md) (AIは直接開発環境を読み取れないため、このファイルで補足すると有効です)
