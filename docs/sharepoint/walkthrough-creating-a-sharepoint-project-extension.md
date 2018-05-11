---
title: 'チュートリアル: SharePoint プロジェクトの拡張機能の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17722233c5215858dce59a0d85a05f668de85446
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>チュートリアル: SharePoint プロジェクトの拡張機能の作成
  このチュートリアルでは、SharePoint プロジェクトの拡張機能を作成する方法について説明します。 プロジェクトの拡張機能を使用して、プロジェクトを追加、削除、または名前を変更する場合など、プロジェクト レベルのイベントに応答することができます。 カスタム プロパティを追加したり、プロパティ値が変更されたときに応答できます。 プロジェクト項目の拡張機能とは異なり、プロジェクトの拡張機能は、特定の SharePoint プロジェクトの種類に関連付けられてすることはできません。 任意の種類の SharePoint プロジェクトを開いたときに、拡張機能を読み込みますプロジェクトの拡張機能を作成するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
 このチュートリアルで作成された任意の SharePoint プロジェクトに追加されるカスタムのブール型プロパティを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 設定すると**True**、新しいプロパティを追加、または、プロジェクトへのイメージ リソース フォルダーにマップします。 設定すると**False**、存在する場合、Images フォルダーが削除されます。 詳細については、次を参照してください。[する方法: 追加し、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   作成する、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]次の処理を SharePoint プロジェクトの拡張機能。  
  
    -   [プロパティ] ウィンドウにカスタム プロジェクトのプロパティを追加します。 プロパティは、任意の SharePoint プロジェクトに適用されます。  
  
    -   SharePoint プロジェクトのオブジェクト モデルを使用すると、プロジェクトにマップされたフォルダーを追加します。  
  
    -   使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]オートメーション オブジェクト モデル (DTE) をプロジェクトからマップされたフォルダーを削除します。  
  
-   ビルド、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension (VSIX) パッケージをプロジェクト プロパティの拡張機能アセンブリを展開します。  
  
-   デバッグとプロジェクトのプロパティをテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、SharePoint と[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**でテンプレート、[!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)]プロジェクト プロパティの拡張機能を配置するための VSIX パッケージを作成します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   プロジェクトの拡張機能を配置するための VSIX パッケージを作成する VSIX プロジェクト。  
  
-   プロジェクトの拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  このノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧でを選択し、 **VSIX プロジェクト**テンプレート。  
  
5.  **名前**ボックスに、入力**ProjectExtensionPackage**を選択し、 **OK**ボタンをクリックします。  
  
     **ProjectExtensionPackage**プロジェクトに表示されます**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**でソリューション ノードのショートカット メニューを開き、**追加**を選択し**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し**Windows**です。  
  
3.  ダイアログ ボックスの上部には、次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧でを選択し、**クラス ライブラリ**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ProjectExtension**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ProjectExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-project"></a>プロジェクトの構成  
 プロジェクトの拡張機能を作成するコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張機能プロジェクトを追加します。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  という名前のコード ファイルを追加**CustomProperty** ProjectExtension プロジェクトにします。  
  
2.  ショートカット メニューを開き、 **ProjectExtension**プロジェクトをクリックして**参照の追加**です。  
  
3.  **参照マネージャー - CustomProperty**  ダイアログ ボックスで、選択、 **Framework**ノード、および、System.ComponentModel.Composition アセンブリおよび System.Windows.Forms アセンブリの横にあるチェック ボックスを選択します。  
  
4.  選択、**拡張機能**ノード、Microsoft.VisualStudio.SharePoint EnvDTE、およびアセンブリの横にあるチェック ボックスをオンにして、 **[ok]**ボタンをクリックします。  
  
5.  **ソリューション エクスプ ローラー**、**参照**用のフォルダー、 **ProjectExtension**プロジェクト**EnvDTE**です。  
  
6.  **プロパティ**ウィンドウで、変更、**相互運用機能型の埋め込み**プロパティを**False**です。  
  
## <a name="defining-the-new-sharepoint-project-property"></a>新しい SharePoint プロジェクトのプロパティを定義します。  
 プロジェクトの拡張機能と、新しいプロジェクト プロパティの動作を定義するクラスを作成します。 新しいプロジェクトの拡張機能をクラスを実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイスです。 SharePoint プロジェクトの拡張機能を定義するときに、このインターフェイスを実装します。 また、追加、<xref:System.ComponentModel.Composition.ExportAttribute>クラスにします。 この属性により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>属性のコンス トラクターを型です。  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>新しい SharePoint プロジェクトのプロパティを定義するには  
  
1.  CustomProperty コード ファイルに次のコードを貼り付けます。  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>ソリューションの構築  
 次に、ソリューションをビルドしてエラーが発生しないがコンパイルされたことを確認してください。  
  
#### <a name="to-build-the-solution"></a>ソリューションをビルドするには  
  
1.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>プロジェクト プロパティの拡張機能を配置するための VSIX パッケージを作成します。  
 プロジェクトの拡張機能を展開するのにには、VSIX パッケージを作成するのにソリューションで VSIX プロジェクトを使用します。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**source.extension.vsixmanifest ファイルのショートカット メニューを開きを選択し、**開く**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] マニフェスト デザイナーで、ファイルを開きます。 表示される情報、**メタデータ**にも表示されます タブ、**拡張機能と更新プログラム**です。 すべての VSIX パッケージでは、extension.vsixmanifest ファイルが必要です。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**カスタム プロジェクト プロパティ**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**カスタム SharePoint プロジェクト プロパティをプロジェクトにイメージ リソース フォルダーへのマッピングを切り替える**です。  
  
5.  選択、**資産** タブをクリックして、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MEFComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
7.  **ソース**一覧で、選択、**現在のソリューション内のプロジェクト**オプション ボタンをクリックします。  
  
8.  **プロジェクト**一覧で、選択**ProjectExtension**です。  
  
     この値は、プロジェクトで作成しているアセンブリの名前を識別します。  
  
9. 選択**OK**を閉じる、**新しいアセットの追加** ダイアログ ボックス。  
  
10. メニュー バーで、次のように選択します。**ファイル**、**すべて保存**終了、マニフェスト デザイナーを閉じると、ときにします。  
  
11. メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**、し、プロジェクトをコンパイル エラーが発生しないことを確認します。  
  
12. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectExtensionPackage**プロジェクトの**ファイル エクスプ ローラーでフォルダーを開く**ボタンをクリックします。  
  
13. **ファイル エクスプ ローラー**ProjectExtensionPackage プロジェクトのビルド出力フォルダーを開き、フォルダーに ProjectExtensionPackage.vsix というファイルが含まれていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="testing-the-project-property"></a>プロジェクト プロパティのテスト  
 カスタム プロジェクト プロパティをテストする準備ができました。 デバッグし、の実験用インスタンスで新しいプロジェクト プロパティの拡張機能をテストする方が簡単[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 このインスタンスの[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSIX またはその他の機能拡張プロジェクトを実行するときに作成します。 プロジェクトをデバッグした後は、システムに、拡張機能のインストールし、続行して、デバッグの通常のインスタンスでテスト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>デバッグし、Visual Studio の実験用インスタンスで拡張機能をテストするには  
  
1.  再起動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]管理者の資格情報と ProjectExtensionPackage ソリューションを開きます。  
  
2.  クリックするか、プロジェクトのデバッグ ビルドを開始、 **f5 キーを押して**キーか、メニュー バーで**デバッグ**、**デバッグの開始**です。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom プロジェクト Property\1.0 に拡張機能をインストールしての実験用インスタンスを起動する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
3.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ファーム ソリューションでは、SharePoint プロジェクトを作成し、ウィザードの他の値の既定値を使用します。  
  
    1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
    2.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、選択**.NET Framework 3.5** .NET Framework のバージョンの一覧にします。  
  
         このバージョンの機能を SharePoint ツール拡張機能が必要、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]です。  
  
    3.  下にある、**テンプレート**ノード、展開、 **Visual c#**または**Visual Basic**  ノードを選択、 **SharePoint**  ノード、を選択し**2010**ノード。  
  
    4.  選択、 **SharePoint 2010 プロジェクト**テンプレート、し、入力**ModuleTest**プロジェクトの名前とします。  
  
4.  **ソリューション エクスプ ローラー**、選択、 **ModuleTest**プロジェクト ノードです。  
  
     新しいカスタム プロパティ**マップ Images フォルダー**に表示されます、**プロパティ** ウィンドウで、既定値は**False**です。  
  
5.  このプロパティの値を変更**True**です。  
  
     イメージ リソース フォルダーは、SharePoint プロジェクトに追加されます。  
  
6.  そのプロパティの値に戻して**False**です。  
  
     選択した場合、 **[はい]**ボタンをクリックして、 **Images フォルダーを削除しますか?**ダイアログ ボックスで、イメージのリソース フォルダーは、SharePoint プロジェクトから削除します。  
  
7.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の実験用インスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクトの拡張](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [SharePoint プロジェクト システムの拡張機能におけるデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [カスタム データの SharePoint ツールの拡張機能への関連付け](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  