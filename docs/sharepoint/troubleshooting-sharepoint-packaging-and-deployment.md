---
caps.handback.revision: 24
---
# SharePoint のパッケージ化と配置のトラブルシューティング
  このトピックでは、SharePoint ソリューションをパッケージ化および配置するときに発生する可能性があるさまざまな問題について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 拡張デバッグの有効化  
 Visual Studio、SharePoint、およびその他のレイヤーの間で問題を診断する場合は、EnableDiagnostics レジストリ キーを使用してスタック トレースを表示することができます。  詳細については、「[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)」を参照してください。  
  
## ソリューション パッケージへのプロジェクト出力の追加  
 パッケージ デザイナーを使用してパッケージにプロジェクト出力を追加することができます。  ただし、プロジェクト出力を追加する際には、そのプロジェクトのプラットフォームが SharePoint ソリューションのプラットフォームと一致していることを確認する必要があります。  SharePoint サーバーに配置するアセンブリに対しては **\[Any CPU\]** プラットフォーム ターゲットを使用することをお勧めします。  詳細については、「[&#91;コンパイル&#93; ページ、プロジェクト デザイナー &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md)」および「[&#91;ビルドの詳細設定&#93; ダイアログ ボックス &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)」を参照してください。  
  
## 検証の警告とエラー  
 Visual Studio の SharePoint 開発ツールでは、ソリューション パッケージが正しい形式になっていることを確認するために検証ステップが実行されます。  特定のフィーチャーやパッケージのためのカスタム検証ステップを作成することもできます。  詳細については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。  
  
## 配置競合の解決  
 SharePoint ソリューションを配置する際に、ソリューション パッケージ内の項目と同じ名前、URL、または ID を持つ項目がサーバー上にあると、競合が発生します。  **\[配置競合の解決\]** プロパティを変更すると、モジュール、Web パーツ、リスト インスタンス、およびコンテンツ タイプの競合を解決するか、報告するか、無視するかを指定できます。  
  
 **\[配置競合の解決\]** プロパティの設定を次の表に示します。  
  
|値|説明|  
|-------|--------|  
|自動|競合を検出して自動的に解決します。|  
|プロンプト|競合を検出し、解決する前に開発者に報告します。|  
|なし。|競合を検出しません。|  
  
## F5 キーによる配置の違い  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を使用してテストおよびデバッグのために SharePoint プロジェクトをローカル SharePoint サーバーに配置する際に、いくつかの追加の手順が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって実行されます。  
  
1.  配置手順の間にインターネット インフォメーション サービス \(IIS\) がリセットされます。  
  
2.  ワークフローが自動的に関連付けられます。  
  
3.  パッケージ デザイナーの階層構造に従ってフィーチャーのアクティブ化の順序が設定されます。  
  
 カスタムの配置手順を追加して F5 キーの動作をさらに変更することもできます。  詳細については、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。  
  
## 可視 Web パーツを配置するときの SharePoint ページの表示の遅延  
 [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)]、[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]、または [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] の Bin フォルダーに可視 Web パーツを配置するときに、SharePoint ページの表示に時間がかかります。  これは、Bin ディレクトリなどの最上位の [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ディレクトリのファイルを変更すると Web アプリケーション全体が再コンパイルされるためです。  結果として、SharePoint ページの表示に最大で 25 秒の遅延が生じます。  
  
### エラー メッセージ  
 なし。  
  
### 解決策  
 この問題を回避するには、次の手順を実行します。  
  
1.  Microsoft サポート オンラインの「[FIX: A hotfix is available to fix two problems in ASP.NET on IIS 7.0 for Windows Vista and Windows Server 2008 \(FIX: Windows Vista および Windows Server 2008 の IIS 7.0 で ASP.NET の 2 つの問題を修正する修正プログラム\)](http://go.microsoft.com/fwlink/?LinkId=179055)」の説明に従って、修正プログラム KB967535 をインストールします。  
  
2.  次の行を Web.config ファイルに追加します。  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## SharePoint プロジェクトの配置が "ソリューションで cab ファイルを抽出できませんでした" というエラーで失敗する  
 いずれかの SharePoint プロジェクト項目の名前にかっこが含まれると、そのソリューションの配置は次のエラーで失敗します。  
  
### エラー メッセージ  
 配置手順 'ソリューションの追加' でエラーが発生しました: ソリューションで cab ファイルを抽出できませんでした  
  
### 解決策  
 この問題を回避するには、SharePoint プロジェクト項目の名前に含まれるかっこを削除してください。  
  
## 別の Web アプリケーションのサイトに可視 Web パーツを配置するとエラーが表示される  
 可視 Web パーツの SiteUrl プロパティを変更することで、Web アプリケーション上のサイトに現在配置されているものとは異なる可視 Web パーツを初めて配置するときに、エラーが発生します。  
  
### エラー メッセージ  
 配置手順 'ソリューションの追加' でエラーが発生しました: ID \[\#\] の機能は既にこのファームにインストールされています。  機能を明示的に再インストールするには、force 属性を使用してください。  
  
### 解決策  
 このエラーは、可視 Web パーツ フィーチャーが SharePoint で取り消される方法によって発生します。  可視 Web パーツを正常に配置するには、F5 キーを押して再度ソリューションを配置してください。  
  
## 入れ子になったユーザー コントロールを配置すると警告が表示される  
 この警告は、ユーザー コントロールを含む可視 Web パーツや、可視 Web パーツや別のユーザー コントロールを含むユーザー コントロールなどの、入れ子になったユーザー コントロールが存在する SharePoint ソリューションを配置したときに発生します。  この警告は、コントロールをツールボックスからデザイナーにドラッグするか、ソース ビューで @Register ディレクティブを使用したときに発生します。  
  
### エラー メッセージ  
 警告 1 要素 '\[*Control Name*\]' は既知の要素ではありません。  Web サイトにコンパイル エラーがあるか、web.config ファイルが存在しない可能性があります。  
  
### 解決策  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクト システムが入れ子になったユーザー コントロールを認識しない場合、Intellisense は使用できず、警告が発行されます。  プロジェクト システムは、プロジェクトがビルドされずにデザイナーが閉じられ、再度開かれた場合、または、デバッグ後に SharePoint ハイブからユーザー コントロールを取り消す自動取り消しオプションが有効な場合は、入れ子になったユーザー コントロールを認識しません。  
  
 この警告を除去するには、プロジェクトをビルドしてからデザイナーを閉じて再度開くか、プロジェクトに対する自動取り消しオプションを無効にします。  これを行うには、\[プロジェクトのプロパティ\] ダイアログ ボックスで、**\[SharePoint\]** タブの **\[デバッグ後に自動取り消し\]** チェック ボックスをオフにします。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  