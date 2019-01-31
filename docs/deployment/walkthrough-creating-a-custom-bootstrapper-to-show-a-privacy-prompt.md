---
title: 'チュートリアル: プライバシー プロンプトを使用のカスタム ブートス トラップの作成 |Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8719f3dc6d892801135d14d093c265445e90fcb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021534"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>チュートリアル: プライバシー プロンプトを使用のカスタム ブートス トラップを作成します。
新しいファイルのバージョンとアセンブリのバージョンのアセンブリが使用可能になると自動的に更新する ClickOnce アプリケーションを構成できます。 お客様がこの動作に同意することを確認するにプライバシー プロンプトを表示できます。 次に、アプリケーションが自動的に更新するアクセス許可を付与するかどうかを選択できます。 アプリケーションが自動的に更新する許可されていない場合はインストールされません。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2010。  
  
## <a name="create-an-update-consent-dialog-box"></a>更新プログラムの同意 ダイアログ ボックスを作成します。  
 プライバシー プロンプトを表示するには、アプリケーションの自動更新に同意するリーダーを要求しているアプリケーションを作成します。  
  
#### <a name="to-create-a-consent-dialog-box"></a>同意ダイアログ ボックスを作成するには  
  
1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
2. **新しいプロジェクト**ダイアログ ボックスで、をクリックして**Windows**、 をクリックし、 **WindowsFormsApplication**。  
  
3. **名前**、型**ConsentDialog**、順にクリックします**OK**します。  
  
4. デザイナーでフォームをクリックします。  
  
5. **プロパティ**ウィンドウで、変更、**テキスト**プロパティを**更新同意ダイアログ**します。  
  
6. **ツールボックス**、展開**すべての Windows フォーム**、ドラッグ、**ラベル**コントロールをフォームにします。  
  
7. デザイナーで、ラベル コントロールをクリックします。  
  
8. **プロパティ**ウィンドウで、変更、**テキスト**のプロパティの **外観**次。  
  
    Web 上の最新の更新プログラムをインストールしようとしているアプリケーションを確認します。 "I Agree"でクリックすると、確認し、インターネットから自動的に更新プログラムをインストールするアプリケーションを承認します。  
  
9. **ツールボックス**、ドラッグ、**チェック ボックスをオン**フォームの中央にコントロール。  
  
10. **プロパティ**ウィンドウで、変更、**テキスト**のプロパティの **レイアウト**に**同意**します。  
  
11. **ツールボックス**、ドラッグ、**ボタン**コントロールをフォームの左下にあります。  
  
12. **プロパティ**ウィンドウで、変更、**テキスト**のプロパティの **レイアウト**に**続行**します。  
  
13. **プロパティ**ウィンドウで、変更、 **(名)** のプロパティの **デザイン**に**ProceedButton**します。  
  
14. **ツールボックス**、ドラッグ、**ボタン**コントロールをフォームの右下にします。  
  
15. **プロパティ**ウィンドウで、変更、**テキスト**のプロパティの **レイアウト**に**キャンセル**します。  
  
16. **プロパティ**ウィンドウで、変更、 **(名)** のプロパティの **デザイン**に**CancelButton**します。  
  
17. デザイナーで、ダブルクリック、**同意**CheckedChanged イベント ハンドラーを生成するチェック ボックスをオンします。  
  
18. Form1 コード ファイルでは、CheckedChanged イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. 更新を無効にするクラスのコンス トラクター、**続行**既定ではボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Form1 コード ファイルでは、エンド ユーザーがオンライン更新に同意した場合に追跡するためにブール値変数に次のコードを追加します。  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. デザイナーで、ダブルクリック、**続行**ボタン クリック イベント ハンドラーを生成します。  
  
22. Form1 コード ファイルでのクリック イベント ハンドラーに次のコードを追加、**続行**ボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. デザイナーで、ダブルクリック、**キャンセル**ボタン クリック イベント ハンドラーを生成します。  
  
24. Form1 コード ファイルでのクリック イベント ハンドラーに次のコードを追加、**キャンセル**ボタンをクリックします。  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. オンライン更新プログラムに、エンドユーザーが同意しない場合は、エラーを返すようアプリケーションを更新します。  
  
     Visual Basic 開発者の場合のみ。  
  
    1. **ソリューション エクスプ ローラー**、 をクリックして**ConsentDialog**します。  
  
    2. **プロジェクト** メニューのをクリックして**モジュールの追加**、 をクリックし、**追加**します。  
  
    3. *Module1.vb*コード ファイルで、次のコードを追加します。  
  
        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4. **プロジェクト** メニューのをクリックして**ConsentDialog プロパティ**、 をクリックし、**アプリケーション**タブ。  
  
    5. オフに**有効にするアプリケーション フレームワーク**します。  
  
    6. **スタートアップ オブジェクト**ドロップダウン メニューで、 **Module1**します。  
  
       > [!NOTE]
       >  アプリケーション フレームワークを無効にするには、Windows XP ビジュアル スタイルのアプリケーション イベント、スプラッシュ スクリーン、単一インスタンス アプリケーションなどの機能が無効にします。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)」を参照してください。  
  
       Visual c# 開発者の場合のみ。  
  
       開く、 *Program.cs*コード ファイル、および次のコードを追加します。  
  
       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. **ビルド** メニューのをクリックして**BuildSolution**します。  
  
## <a name="create-the-custom-bootstrapper-package"></a>カスタム ブートス トラップ パッケージを作成します。  
 プライバシー プロンプトをエンドユーザーに表示するには、更新プログラムの同意ダイアログ アプリケーション用のカスタム ブートス トラップ パッケージを作成し、ClickOnce アプリケーションのすべての前提条件として含めます。  
  
 この手順では、次のドキュメントを作成してカスタム ブートス トラップ パッケージを作成する方法を示します。  
  
-   A *product.xml*ブートス トラップの内容を記述するマニフェスト ファイル。  
  
-   A *package.xml*マニフェスト ファイルを文字列と、ソフトウェア ライセンス条項など、パッケージのローカライズに固有の要素を一覧表示します。  
  
-   ソフトウェアのライセンス条項のドキュメントです。  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>手順 1: ブートス トラップ ディレクトリを作成するには  
  
1.  という名前のディレクトリを作成する**UpdateConsentDialog**で、 *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*します。  
  
    > [!NOTE]
    >  このフォルダーを作成する管理者特権を必要があります。  
  
2.  *UpdateConsentDialog*ディレクトリ、サブディレクトリを作成*en*します。  
  
    > [!NOTE]
    >  ロケールごとに新しいディレクトリを作成します。 たとえば、フランス、ドイツのロケールのサブディレクトリを追加できます。 必要に応じて、フランス語、ドイツ語の文字列と言語パック、これらのディレクトリが含まれます。  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>手順 2: Product.xml マニフェスト ファイルを作成するには  
  
1.  という名前のテキスト ファイルを作成する*product.xml*します。  
  
2.  *Product.xml*ファイルに、次の XML コードを追加します。 既存の XML コードを上書きしないことを確認します。  
  
    ```xml  
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
  
3.  UpdateConsentDialog ブートス トラップ ディレクトリに保存します。  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>手順 3: Package.xml のマニフェスト ファイルと、ソフトウェア ライセンス条項を作成するには  
  
1.  という名前のテキスト ファイルを作成する*package.xml*します。  
  
2.  *Package.xml*ファイルに、ロケールを定義し、ソフトウェア ライセンス条項を含めるには、次の XML コードを追加します。 既存の XML コードを上書きしないことを確認します。  
  
    ```xml  
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
  
3.  UpdateConsentDialog ブートス トラップ ディレクトリに en サブディレクトリに保存します。  
  
4.  という名前のドキュメントを作成する*eula.rtf*のソフトウェア使用許諾条件。  
  
    > [!NOTE]
    >  ソフトウェアのライセンス条項は、ライセンス、保証、負債、および現地の法律に関する情報を含める必要があります。 これらのファイルは、ロケール固有のもの、MBCS または UNICODE 文字をサポートする形式でファイルを保存するようにする必要があります。 ソフトウェアのライセンス条項のコンテンツについて、法務部門を参照してください。  
  
5.  En のサブディレクトリにドキュメントを保存、 *UpdateConsentDialog*ブートス トラップ ディレクトリ。  
  
6.  必要に応じて、作成、新しい*package.xml*マニフェストのファイルと新しい*eula.rtf*各ロケールのソフトウェア ライセンス条項のドキュメント。 たとえば、fr および de ロケールのサブディレクトリを作成した場合は、package.xml 個別マニフェスト ファイルおよびソフトウェア ライセンス条項を作成し、fr および de サブディレクトリに保存します。  
  
## <a name="set-the-update-consent-application-as-a-prerequisite"></a>前提条件としての更新プログラムの同意を求めるアプリケーションを設定します。  
 Visual Studio で、前提条件として、更新プログラムの同意を求めるアプリケーションを設定できます。  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>前提条件として更新プログラムの同意を求めるアプリケーションを設定するには  
  
1.  **ソリューション エクスプ ローラー**、展開するアプリケーションの名前をクリックします。  
  
2.  **[プロジェクト]** メニューの *ProjectName* の **[プロパティ]** をクリックします。  
  
3.  をクリックして、**発行**] ページの [クリックして**の前提条件**します。  
  
4.  選択**同意ダイアログを更新**します。  
  
    > [!NOTE]
    >  前提条件 ダイアログ ボックスで更新プログラムの同意ダイアログを表示する Visual Studio を閉じて再度開くことがあります。  
  
5.  **[OK]** をクリックします。  
  
## <a name="create-and-test-the-setup-program"></a>作成し、セットアップ プログラムをテスト  
 前提条件として、更新プログラムの同意を求めるアプリケーションを設定した後、アプリケーションのインストーラーとブートス トラップを生成できます。  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>同意を作成していないをクリックしてセットアップ プログラムをテストするには  
  
1.  **ソリューション エクスプ ローラー**、展開するアプリケーションの名前をクリックします。  
  
2.  **[プロジェクト]** メニューの *ProjectName* の **[プロパティ]** をクリックします。  
  
3.  をクリックして、**発行**] ページの [クリックして**今すぐ発行**します。  
  
4.  発行の出力が自動的に開かない場合は、発行の出力に移動します。  
  
5.  実行、 *Setup.exe*プログラム。  
  
     セットアップ プログラムは、同意ダイアログの更新プログラムのソフトウェア使用許諾契約書を示しています。  
  
6.  ソフトウェア ライセンス条項を読み、クリックして**Accept**します。  
  
     更新プログラムの同意ダイアログ アプリケーションの表示および次のテキストが表示されます。Web 上の最新の更新プログラムをインストールしようとしているアプリケーションを確認します。 同意でクリックするは、インターネット上に自動的に更新プログラムを確認するアプリケーションを承認します。  
  
7.  アプリケーションを閉じるか、[キャンセル] をクリックします。  
  
     アプリケーションは、エラーを示しています。システム コンポーネントのインストール中にエラーが発生しました。 *ApplicationName*します。 すべてのシステム コンポーネントが正常にインストールされるまで、セットアップを続行できません。  
  
8.  次のエラー メッセージを表示する詳細をクリックします。コンポーネント更新プログラムの同意 ダイアログ ボックスは、次のエラー メッセージでのインストールに失敗しました。「自動更新の契約に同意がありません」。 次のコンポーネントがインストールに失敗しました-更新プログラムの同意 ダイアログ。  
  
9. **[閉じる]** をクリックします。  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>同意を作成してクリックして、セットアップ プログラムをテスト、するには  
  
1.  **ソリューション エクスプ ローラー**、展開するアプリケーションの名前をクリックします。  
  
2.  **[プロジェクト]** メニューの *ProjectName* の **[プロパティ]** をクリックします。  
  
3.  をクリックして、**発行**] ページの [クリックして**今すぐ発行**します。  
  
4.  発行の出力が自動的に開かない場合は、発行の出力に移動します。  
  
5.  実行、 *Setup.exe*プログラム。  
  
     セットアップ プログラムは、同意ダイアログの更新プログラムのソフトウェア使用許諾契約書を示しています。  
  
6.  ソフトウェア ライセンス条項を読み、クリックして**Accept**します。  
  
     更新プログラムの同意ダイアログ アプリケーションの表示および次のテキストが表示されます。Web 上の最新の更新プログラムをインストールしようとしているアプリケーションを確認します。 同意でクリックするは、インターネット上に自動的に更新プログラムを確認するアプリケーションを承認します。  
  
7.  をクリックして**同意**、 をクリックし、**続行**します。  
  
     アプリケーションは、インストールを開始します。  
  
8.  アプリケーションのインストール ダイアログ ボックスが表示されたら、クリックして**インストール**します。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)   
 [ブートストラップ パッケージの作成](../deployment/creating-bootstrapper-packages.md)   
 [方法: 製品マニフェストを作成する](../deployment/how-to-create-a-product-manifest.md)   
 [方法: パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)