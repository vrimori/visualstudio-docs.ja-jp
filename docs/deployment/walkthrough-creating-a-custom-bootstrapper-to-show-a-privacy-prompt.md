---
title: "チュートリアル: プライバシー プロンプトを表示するためのカスタム ブートストラップの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, 必要条件"
  - "依存関係 [.NET Framework], カスタム ブートストラップ パッケージ"
  - "配置 (アプリケーションを) [Visual Studio], カスタムの必須コンポーネント"
  - "必要条件 [.NET Framework], カスタム ブートストラップ パッケージ"
  - "Windows インストーラーの配置, 必要条件"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル: プライバシー プロンプトを表示するためのカスタム ブートストラップの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce アプリケーションは、アセンブリに含まれるファイルおよびアセンブリの新しいバージョンが利用できるようになったときに自動的に更新されるように構成できます。  この動作に同意することをユーザーに確認するには、プライバシー プロンプトを表示します。  このプロンプトで、ユーザーはアプリケーションの自動更新を許可するかどうかを選択できます。  アプリケーションの自動更新が許可されなかった場合、インストールは行われません。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2010  
  
## 更新の同意を求めるダイアログ ボックスを作成する  
 プライバシー プロンプトを表示するには、アプリケーションの自動更新についてユーザーの同意を求めるアプリケーションを作成します。  
  
#### 同意を求めるダイアログ ボックスを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[ウィンドウ\]** をクリックし、**\[Windows フォーム アプリケーション\]** をクリックします。  
  
3.  **\[名前\]** に「ConsentDialog」と入力し、**\[OK\]** をクリックします。  
  
4.  デザイナーでフォームをクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、**Text** プロパティを「Update Consent Dialog」に変更します。  
  
6.  **ツールボックス**で **\[すべての Windows フォーム\]** を展開し、**Label** コントロールをフォームにドラッグします。  
  
7.  デザイナーでラベル コントロールをクリックします。  
  
8.  **\[プロパティ\]** ウィンドウで、**Appearance** の **Text** プロパティを次のように変更します。  
  
     インストールしようとしているアプリケーションでは、Web で最新の更新プログラムがチェックされます。  \[同意する\] をクリックして承認すると、インターネットに接続して自動的に更新プログラムの確認とインストールが行われます。  
  
9. **ツールボックス**の **Checkbox** コントロールをフォームの中央にドラッグします。  
  
10. **\[プロパティ\]** ウィンドウで、**Layout** の **Text** プロパティを「同意する」に変更します。  
  
11. **ツールボックス**の **Button** コントロールをフォームの左下へドラッグします。  
  
12. **\[プロパティ\]** ウィンドウで、**Layout** の **Text** プロパティを「続行」に変更します。  
  
13. **\[プロパティ\]** ウィンドウで、**Design** の **\(Name\)** プロパティを「ProceedButton」に変更します。  
  
14. **ツールボックス**の **Button** コントロールをフォームの右下へドラッグします。  
  
15. **\[プロパティ\]** ウィンドウで、**Layout** の **Text** プロパティを「キャンセル」に変更します。  
  
16. **\[プロパティ\]** ウィンドウで、**Design** の **\(Name\)** プロパティを「CancelButton」に変更します。  
  
17. デザイナーで、**\[同意する\]** チェック ボックスをダブルクリックして、CheckedChanged イベント ハンドラーを生成します。  
  
18. Form1 コード ファイルで、CheckedChanged イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. クラス コンストラクターを更新して、**\[続行\]** ボタンを既定で無効にします。  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Form1 コード ファイルで、エンド ユーザーがオンライン更新に同意したかどうかをブール変数で追跡するために次のコードを追加します。  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. デザイナーで、**\[続行\]** ボタンをダブルクリックして、Click イベント ハンドラーを生成します。  
  
22. Form1 コード ファイルで、**\[続行\]** ボタンの Click イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. デザイナーで、**\[キャンセル\]** ボタンをダブルクリックして、Click イベント ハンドラーを生成します。  
  
24. Form1 コード ファイルで、**\[キャンセル\]** ボタンの Click イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. アプリケーションを更新して、エンド ユーザーがオンライン更新に同意しなかった場合にエラーを返すようにします。  
  
     Visual Basic 開発者用の手順は次のとおりです。  
  
    1.  **ソリューション エクスプローラー**で、**\[ConsentDialog\]** をクリックします。  
  
    2.  **\[プロジェクト\]** メニューの **\[モジュールの追加\]** をクリックし、**\[追加\]** をクリックします。  
  
    3.  Module1.vb コード ファイルで、次のコードを追加します。  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  **\[プロジェクト\]** メニューの **\[ConsentDialog のプロパティ\]** をクリックし、**\[アプリケーション\]** タブをクリックします。  
  
    5.  **\[アプリケーション フレームワークを有効にする\]** チェック ボックスをオフにします。  
  
    6.  **\[スタートアップ オブジェクト\]** ドロップダウン メニューの **\[Module1\]** を選択します。  
  
        > [!NOTE]
        >  アプリケーション フレームワークを無効にすると、Windows XP の視覚スタイル、アプリケーション イベント、スプラッシュ スクリーン、単一インスタンス アプリケーションなどの機能は無効になります。  詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)」を参照してください。  
  
     C\# 開発者用の手順は次のとおりです。  
  
     Program.cs コード ファイルを開いて、次のコードを追加します。  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## カスタム ブートストラップ パッケージを作成する  
 エンド ユーザーにプライバシー プロンプトを表示するには、更新の同意を求めるダイアログを表示するアプリケーションのカスタム ブートスラップ パッケージを作成し、必須コンポーネントとしてすべての ClickOnce アプリケーションに含めます。  
  
 ここでは、次のドキュメントを作成してカスタム ブートストラップ パッケージを作成する方法を示します。  
  
-   ブートスラップの内容を記述した product.xml マニフェスト ファイル。  
  
-   パッケージのローカリゼーション固有の特性 \(文字列、ソフトウェア ライセンス条項など\) を記述した package.xml マニフェスト ファイル。  
  
-   ソフトウェア ライセンス条項のドキュメント。  
  
#### 手順 1: ブートストラップ ディレクトリを作成するには  
  
1.  UpdateConsentDialog という名前のディレクトリを %PROGRAMFILES%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages に作成します。  
  
    > [!NOTE]
    >  このフォルダーを作成するには、管理特権が必要な場合があります。  
  
2.  UpdateConsentDialog ディレクトリに「en」という名前のサブディレクトリを作成します。  
  
    > [!NOTE]
    >  ロケールごとに新しいディレクトリを作成します。  たとえば、fr および de のロケールのサブディレクトリを作成し、  必要に応じて、フランス語とドイツ語の文字列や言語パックを含めることができます。  
  
#### 手順 2: product.xml マニフェスト ファイルを作成するには  
  
1.  `product.xml` というテキスト ファイルを作成します。  
  
2.  product.xml ファイルに次の XML コードを追加します。  既存の XML コードは上書きしないように注意してください。  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  ファイルを UpdateConsentDialog ブートストラップ ディレクトリに保存します。  
  
#### 手順 3: package.xml マニフェスト ファイルとソフトウェア ライセンス条項を作成するには  
  
1.  `package.xml` というテキスト ファイルを作成します。  
  
2.  package.xml ファイルに次の XML コードを追加して、ロケールを定義し、ソフトウェア ライセンス条項を含めます。  既存の XML コードは上書きしないように注意してください。  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  ファイルを UpdateConsentDialog ブートストラップ ディレクトリの en サブディレクトリに保存します。  
  
4.  eula.rtf というソフトウェア ライセンス条項のドキュメントを作成します。  
  
    > [!NOTE]
    >  ソフトウェア ライセンス条項には、ライセンス、保証、責任、法律などに関する情報を含めます。  これらのファイルはロケール固有の内容にする必要があるため、MBCS または UNICODE の文字をサポートするファイル形式で保存します。  ソフトウェア ライセンス条項の内容については、法務部に確認してください。  
  
5.  ドキュメントを UpdateConsentDialog ブートストラップ ディレクトリの en サブディレクトリに保存します。  
  
6.  必要に応じて、ロケールごとに新しい package.xml マニフェスト ファイルと新しいソフトウェア ライセンス条項の eula.rtf ドキュメントを作成します。  たとえば、fr と de のロケールのサブディレクトリを作成した場合、それぞれの package.xml マニフェスト ファイルとソフトウェア ライセンス条項を作成し、fr サブディレクトリと de サブディレクトリにそれぞれ保存します。  
  
## 更新の同意を求めるアプリケーションを必須コンポーネントとして設定する  
 Visual Studio で、更新の同意を求めるアプリケーションを必須コンポーネントとして設定できます。  
  
#### 更新の同意を求めるアプリケーションを必須コンポーネントとして設定するには  
  
1.  **ソリューション エクスプローラー**で、配置するアプリケーションの名前をクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[*プロジェクト名*のプロパティ\]** をクリックします。  
  
3.  **\[発行\]** ページをクリックし、**\[必須コンポーネント\]** をクリックします。  
  
4.  **\[Update Consent Dialog\]** を選択します。  
  
    > [!NOTE]
    >  Visual Studio をいったん閉じて開き直さないと \[必須コンポーネント\] ダイアログ ボックスに Update Consent Dialog が表示されない場合があります。  
  
5.  **\[OK\]** をクリックします。  
  
## セットアップ プログラムを作成してテストする  
 更新の同意を求めるアプリケーションを必須コンポーネントとして設定したら、アプリケーションのインストーラーとブートストラップを生成できます。  
  
#### セットアップ プログラムを作成して \[同意する\] をクリックしない場合の動作をテストするには  
  
1.  **ソリューション エクスプローラー**で、配置するアプリケーションの名前をクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[*プロジェクト名*のプロパティ\]** をクリックします。  
  
3.  **\[発行\]** ページをクリックし、**\[今すぐ発行\]** をクリックします。  
  
4.  発行の出力が自動的に開かない場合は発行の出力に移動します。  
  
5.  Setup.exe プログラムを実行します。  
  
     セットアップ プログラムで、Update Consent Dialog のソフトウェア ライセンス条項が表示されます。  
  
6.  ソフトウェア ライセンス条項を読み、**\[同意する\]** をクリックします。  
  
     Update Consent Dialog アプリケーションが表示され、"インストールしようとしているアプリケーションでは、Web で最新の更新プログラムがチェックされます。  \[同意する\] をクリックして承認すると、インターネットに接続して自動的に更新プログラムの確認とインストールが行われます。" というテキストが表示されます。  
  
7.  アプリケーションを閉じるか、\[キャンセル\] をクリックします。  
  
     アプリケーションで、"*ApplicationName* のシステム コンポーネントのインストール中にエラーが発生しました。  すべてのシステム コンポーネントが正常にインストールされるまで、セットアップは続行できません。" というエラーが表示されます。  
  
8.  \[詳細\] をクリックします。"コンポーネント Update Consent Dialog のインストールに失敗し、次のエラー メッセージが生成されました: "The automatic update agreement is not accepted."次のコンポーネントをインストールできませんでした: \- Update Consent Dialog" というエラー メッセージが表示されます。  
  
9. **\[閉じる\]** をクリックします。  
  
#### セットアップ プログラムを作成して \[同意する\] をクリックした場合の動作をテストするには  
  
1.  **ソリューション エクスプローラー**で、配置するアプリケーションの名前をクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[*プロジェクト名*のプロパティ\]** をクリックします。  
  
3.  **\[発行\]** ページをクリックし、**\[今すぐ発行\]** をクリックします。  
  
4.  発行の出力が自動的に開かない場合は発行の出力に移動します。  
  
5.  Setup.exe プログラムを実行します。  
  
     セットアップ プログラムで、Update Consent Dialog のソフトウェア ライセンス条項が表示されます。  
  
6.  ソフトウェア ライセンス条項を読み、**\[同意する\]** をクリックします。  
  
     Update Consent Dialog アプリケーションが表示され、"インストールしようとしているアプリケーションでは、Web で最新の更新プログラムがチェックされます。  \[同意する\] をクリックして承認すると、インターネットに接続して自動的に更新プログラムの確認とインストールが行われます。" というテキストが表示されます。  
  
7.  **\[同意する\]** をクリックし、**\[続行\]** をクリックします。  
  
     アプリケーションでインストールが開始されます。  
  
8.  \[アプリケーションのインストール\] ダイアログ ボックスで、**\[インストール\]** をクリックします。  
  
## 参照  
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)   
 [ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)   
 [方法: 製品マニフェストを作成する](../deployment/how-to-create-a-product-manifest.md)   
 [方法: パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)