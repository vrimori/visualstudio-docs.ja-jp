---
title: 'チュートリアル: プライバシー プロンプトを表示するためのカスタム ブートス トラップの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6f20389e0487fd548ac239503faae01adb7dbdf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>チュートリアル: プライバシー プロンプトを表示するためのカスタム ブートストラップの作成
新しいファイルおよびアセンブリのバージョンを持つアセンブリが使用可能になると自動的に更新する ClickOnce アプリケーションを構成することができます。 をお客様がこれに同意することを確認するために、プライバシー プロンプトを表示できます。 次に、自動的に更新するアプリケーションへのアクセス許可を付与するかどうかを選択できます。 アプリケーションが自動的に更新する許可されていない場合はインストールされません。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2010。  
  
## <a name="creating-an-update-consent-dialog-box"></a>更新プログラムの同意 ダイアログ ボックスを作成します。  
 プライバシー プロンプトを表示するには、アプリケーションの自動更新することに同意を求める、アプリケーションを作成します。  
  
#### <a name="to-create-a-consent-dialog-box"></a>同意を求めるダイアログ ボックスを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、をクリックして**Windows**、クリックして**WindowsFormsApplication**です。  
  
3.  **名前**、型**ConsentDialog**、順にクリック**OK**です。  
  
4.  デザイナーでフォームをクリックします。  
  
5.  **プロパティ**ウィンドウで、変更、**テキスト**プロパティを**更新同意を求めるダイアログ**です。  
  
6.  **ツールボックス**、展開**すべての Windows フォーム**、ドラッグ、**ラベル**をフォームにコントロールです。  
  
7.  デザイナーで、ラベル コントロールをクリックします。  
  
8.  **プロパティ**ウィンドウで、変更、**テキスト**プロパティの **外観**以下。  
  
     インストールしようとしているアプリケーションは、Web 上の最新の更新プログラムをチェックします。 「同意」をクリックするでは、アプリケーションを確認し、インターネットから更新プログラムを自動的にインストールを承認します。  
  
9. **ツールボックス**、ドラッグ、**チェック**フォームの中央にコントロールです。  
  
10. **プロパティ**ウィンドウで、変更、**テキスト**プロパティの **レイアウト**に**同意**です。  
  
11. **ツールボックス**、ドラッグ、**ボタン**コントロールをフォームの左下にします。  
  
12. **プロパティ**ウィンドウで、変更、**テキスト**プロパティの **レイアウト**に**続行**です。  
  
13. **プロパティ**ウィンドウで、変更、 **(名)**プロパティの **デザイン**に**ProceedButton**です。  
  
14. **ツールボックス**、ドラッグ、**ボタン**コントロールをフォームの右下にします。  
  
15. **プロパティ**ウィンドウで、変更、**テキスト**プロパティの **レイアウト**に**キャンセル**です。  
  
16. **プロパティ**ウィンドウで、変更、 **(名)**プロパティの **デザイン**に**CancelButton**です。  
  
17. デザイナーをダブルクリックして、**同意**CheckedChanged イベント ハンドラーを生成する チェック ボックスです。  
  
18. Form1 コード ファイルでは、次の CheckedChanged イベント ハンドラーのコードを追加します。  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. 更新を無効にするクラスのコンス トラクター、**続行**既定ボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Form1 コード ファイルでは、エンドユーザーがオンライン更新に同意した場合は、追跡するブール値変数に次のコードを追加します。  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. デザイナーをダブルクリックして、**続行**ボタン クリック イベント ハンドラーを生成します。  
  
22. Form1 コード ファイル内の Click イベント ハンドラーに次のコードを追加、**続行**ボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. デザイナーをダブルクリックして、**キャンセル**ボタン クリック イベント ハンドラーを生成します。  
  
24. Form1 コード ファイル内のクリック イベント ハンドラーに次のコードを追加、**キャンセル**ボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. アプリケーションを更新して、エンドユーザーがオンライン更新に同意しない場合、エラーを返します。  
  
     Visual Basic 開発者の場合のみ。  
  
    1.  **ソリューション エクスプ ローラー**をクリックして**ConsentDialog**です。  
  
    2.  **プロジェクト** メニューのをクリックして**モジュールの追加**、クリックして**追加**です。  
  
    3.  Module1.vb コード ファイルでは、次のコードを追加します。  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  **プロジェクト** メニューのをクリックして**ConsentDialog プロパティ**、をクリックし、**アプリケーション**タブです。  
  
    5.  オフにして**有効にするアプリケーション フレームワーク**です。  
  
    6.  **スタートアップ オブジェクト**ドロップダウン メニューで、 **Module1**です。  
  
        > [!NOTE]
        >  アプリケーション フレームワークを無効にするには、Windows XP の視覚スタイル、アプリケーション イベント、スプラッシュ スクリーン、単一インスタンス アプリケーションなどの機能が無効にします。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)」を参照してください。  
  
     Visual c# 開発者の場合のみ。  
  
     Program.cs コード ファイルを開き、次のコードを追加します。  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. **ビルド**] メニューのをクリックして**[ソリューションのビルド**です。  
  
## <a name="creating-the-custom-bootstrapper-package"></a>カスタム ブートス トラップ パッケージを作成します。  
 エンドユーザーに、プライバシー プロンプトを表示するには、同意を求めるダイアログの更新アプリケーション用のカスタム ブートス トラップ パッケージを作成し、ClickOnce アプリケーションのすべての前提条件として含めるです。  
  
 この手順では、次のドキュメントを作成することで、カスタム ブートス トラップ パッケージを作成する方法を示します。  
  
-   Product.xml マニフェストのファイルに、ブートス トラップの内容を記述します。  
  
-   文字列と、ソフトウェア ライセンス条項など、パッケージのローカライズに固有の要素の一覧を表示する package.xml のマニフェスト ファイル。  
  
-   ソフトウェア ライセンス条項のドキュメントです。  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>手順 1: ブートス トラップ ディレクトリを作成するには  
  
1.  という名前のディレクトリを作成する**UpdateConsentDialog** %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages にします。  
  
    > [!NOTE]
    >  このフォルダーを作成する管理者特権を必要があります。  
  
2.  UpdateConsentDialog ディレクトリでは、en という名前のサブディレクトリを作成します。  
  
    > [!NOTE]
    >  ロケールごとに新しいディレクトリを作成します。 たとえば、fr および de ロケールのサブディレクトリを追加することができます。 必要に応じて、フランス語とドイツ語の文字列と言語パック、これらのディレクトリが含まれます。  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>手順 2: product.xml マニフェスト ファイルを作成するには  
  
1.  という名前のテキスト ファイルを作成する`product.xml`です。  
  
2.  Product.xml ファイルでは、次の XML コードを追加します。 既存の XML コードを上書きしないことを確認します。  
  
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
  
3.  UpdateConsentDialog ブートス トラップ ディレクトリにファイルを保存します。  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>手順 3: package.xml マニフェストを作成するには、ファイルと、ソフトウェア ライセンス条項  
  
1.  という名前のテキスト ファイルを作成する`package.xml`です。  
  
2.  Package.xml ファイルでは、ロケールを定義し、ソフトウェア ライセンス条項を含めるには、次の XML コードを追加します。 既存の XML コードを上書きしないことを確認します。  
  
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
  
3.  UpdateConsentDialog ブートス トラップ ディレクトリに en サブディレクトリにファイルを保存します。  
  
4.  ソフトウェア ライセンス条項 eula.rtf というドキュメントを作成します。  
  
    > [!NOTE]
    >  ソフトウェア ライセンス条項は、ライセンス、保証、負債、および地域の法律によってに関する情報を含める必要があります。 これらのファイルはロケール固有、MBCS または UNICODE 文字をサポートする形式でファイルを保存するかどうかを必ずようにする必要があります。 ソフトウェア ライセンス条項のコンテンツに関する法務部門に問い合わせてください。  
  
5.  UpdateConsentDialog ブートス トラップ ディレクトリに en サブディレクトリに、ドキュメントを保存します。  
  
6.  必要に応じて、各ロケールのソフトウェア ライセンス条項を新しい package.xml マニフェスト ファイルと新しい eula.rtf ドキュメントを作成します。 たとえば、fr および de ロケールのサブディレクトリを作成する場合は、package.xml 個別マニフェスト ファイルおよびソフトウェア ライセンス条項を作成し、fr および de サブディレクトリに保存します。  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>前提条件として更新プログラムの同意を求めるアプリケーションの設定  
 Visual Studio で、前提条件として更新プログラムの同意を求めるアプリケーションを設定できます。  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>前提条件として更新プログラムの同意を求めるアプリケーションを設定するには  
  
1.  **ソリューション エクスプ ローラー**を展開する、アプリケーションの名前をクリックします。  
  
2.  **プロジェクト** メニューのをクリックして*ProjectName* **プロパティ**です。  
  
3.  クリックして、**発行** ページで、クリックして**の前提条件**です。  
  
4.  選択**同意ダイアログを更新**です。  
  
    > [!NOTE]
    >  必須コンポーネント ダイアログ ボックスで更新プログラムの同意を求めるダイアログを表示する Visual Studio を閉じて再度開くことがあります。  
  
5.  **[OK]**をクリックします。  
  
## <a name="creating-and-testing-the-setup-program"></a>作成して、セットアップ プログラムをテストします。  
 前提条件として更新プログラムの同意を求めるアプリケーションを設定した後、アプリケーションのインストーラーとブートス トラップを生成できます。  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>作成していない をクリックして、セットアップ プログラムをテストするには、ことに同意します。  
  
1.  **ソリューション エクスプ ローラー**を展開する、アプリケーションの名前をクリックします。  
  
2.  **プロジェクト** メニューのをクリックして*ProjectName* **プロパティ**です。  
  
3.  クリックして、**発行**] ページで、クリックして**[今すぐ発行**です。  
  
4.  発行の出力が自動的に開かない場合は、発行の出力に移動します。  
  
5.  Setup.exe プログラムを実行します。  
  
     セットアップ プログラムは、更新プログラムの同意ダイアログのソフトウェア使用許諾契約書を示しています。  
  
6.  ソフトウェアの使用許諾契約を読み、クリックして**Accept**です。  
  
     更新プログラムの同意ダイアログ アプリケーションが表示され、次のテキスト: インストールしようとしているアプリケーションが Web 上の最新の更新プログラムをチェックします。 同意をクリックするでは、インターネットに自動的に更新プログラムを確認するためのアプリケーションを承認します。  
  
7.  アプリケーションを閉じるか、[キャンセル] をクリックします。  
  
     アプリケーションはエラーを示します: のシステム コンポーネントのインストール中にエラーが発生しました。 *ApplicationName*です。 すべてのシステム コンポーネントが正常にインストールされるまで、セットアップを続行できません。  
  
8.  次のエラー メッセージを表示するための詳細 をクリックします。 コンポーネントの更新に同意するもののダイアログ ボックスは、次のエラー メッセージとインストールに失敗しました:"自動更新の契約に同意しない"です。 次のコンポーネントがインストールに失敗しました:-更新プログラムの同意ダイアログ  
  
9. **[閉じる]** をクリックします。  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>作成しをクリックして、セットアップ プログラムをテストするには、ことに同意します。  
  
1.  **ソリューション エクスプ ローラー**を展開する、アプリケーションの名前をクリックします。  
  
2.  **プロジェクト** メニューのをクリックして*ProjectName* **プロパティ**です。  
  
3.  クリックして、**発行**] ページで、クリックして**[今すぐ発行**です。  
  
4.  発行の出力が自動的に開かない場合は、発行の出力に移動します。  
  
5.  Setup.exe プログラムを実行します。  
  
     セットアップ プログラムは、更新プログラムの同意ダイアログのソフトウェア使用許諾契約書を示しています。  
  
6.  ソフトウェアの使用許諾契約を読み、クリックして**Accept**です。  
  
     更新プログラムの同意ダイアログ アプリケーションが表示され、次のテキスト: インストールしようとしているアプリケーションが Web 上の最新の更新プログラムをチェックします。 同意をクリックするでは、インターネットに自動的に更新プログラムを確認するためのアプリケーションを承認します。  
  
7.  をクリックして**同意**、クリックして**続行**です。  
  
     アプリケーションは、インストールを開始します。  
  
8.  アプリケーションのインストール ダイアログ ボックスが表示されたら、クリックして**インストール**です。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)   
 [ブートス トラップ パッケージを作成します。](../deployment/creating-bootstrapper-packages.md)   
 [方法: 製品マニフェストを作成します。](../deployment/how-to-create-a-product-manifest.md)   
 [方法: パッケージ マニフェストを作成します。](../deployment/how-to-create-a-package-manifest.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)