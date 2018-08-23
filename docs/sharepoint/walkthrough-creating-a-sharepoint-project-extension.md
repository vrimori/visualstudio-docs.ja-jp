---
title: 'チュートリアル: SharePoint プロジェクト拡張機能の作成 |Microsoft Docs'
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
ms.openlocfilehash: b8620a51480868302fc840bffea5bbdb427c48f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635617"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>チュートリアル: SharePoint プロジェクト拡張機能を作成します。
  このチュートリアルでは、SharePoint プロジェクトの拡張機能を作成する方法について説明します。 プロジェクトの拡張機能を使用すると、プロジェクトを追加、削除、または名前を変更する場合など、プロジェクト レベルのイベントに応答します。 カスタム プロパティを追加またはプロパティ値を変更するときの応答もできます。 プロジェクト項目の拡張機能とは異なりプロジェクト拡張機能は、特定の SharePoint プロジェクトの種類に関連付けすることはできません。 任意の種類の SharePoint プロジェクトを開いたときに、拡張機能を読み込むプロジェクトの拡張機能を作成するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
 このチュートリアルで作成された SharePoint プロジェクトに追加されるカスタムのブール型プロパティを作成します[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 設定すると**True**、新しいプロパティを追加、または、プロジェクトのイメージ リソース フォルダーにマップします。 設定すると**False**、Images フォルダーを削除、存在する場合。 詳細については、次を参照してください。[方法: 追加すると、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   作成、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]実行すると、次の SharePoint プロジェクト拡張機能。  
  
    -   [プロパティ] ウィンドウには、カスタムのプロジェクトのプロパティを追加します。 プロパティは、任意の SharePoint プロジェクトに適用されます。  
  
    -   SharePoint プロジェクト オブジェクト モデルを使用すると、プロジェクトにマップされたフォルダーを追加します。  
  
    -   使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]オートメーション オブジェクト モデル (DTE) をプロジェクトからマップされたフォルダーを削除します。  
  
-   構築、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension (VSIX) パッケージ、プロジェクト プロパティの拡張機能アセンブリを展開します。  
  
-   デバッグとプロジェクトのプロパティをテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、SharePoint と[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**テンプレート、[!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)]プロジェクト プロパティの拡張機能を配置するための VSIX パッケージを作成します。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   プロジェクトの拡張機能を配置するための VSIX パッケージを作成する VSIX プロジェクト。  
  
-   プロジェクトの拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選択し、**機能拡張**ノード。  
  
    > [!NOTE]  
    >  このノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧で選択し、 **VSIX プロジェクト**テンプレート。  
  
5.  **名前**ボックスに、入力**ProjectExtensionPackage**、選択し、 **OK**ボタン。  
  
     **ProjectExtensionPackage**プロジェクトに表示されます**ソリューション エクスプ ローラー**します。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソリューション ノードのショートカット メニューを開き、**追加**を選び、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#** または**Visual Basic**ノードを選び、 **Windows**します。  
  
3.  ダイアログ ボックスの上部にある次のように選択します。 **.NET Framework 4.5** 、.NET Framework のバージョンの一覧で選択し、**クラス ライブラリ**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ProjectExtension**、選択し、 **OK**ボタン。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **ProjectExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
5.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configure-the-project"></a>プロジェクトを構成する
 プロジェクトの拡張機能を作成するコードを記述する前に、コード ファイルと拡張機能プロジェクトにアセンブリ参照を追加します。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  というコード ファイルを追加**CustomProperty** ProjectExtension プロジェクトへです。  
  
2.  ショートカット メニューを開き、 **ProjectExtension**プロジェクトを選び、**参照の追加**します。  
  
3.  **参照マネージャー - CustomProperty**  ダイアログ ボックスで、選択、 **Framework**ノード、し、System.ComponentModel.Composition および System.Windows.Forms アセンブリの横にあるチェック ボックスを選択します。  
  
4.  選択、**拡張機能**ノードが、Microsoft.VisualStudio.SharePoint および EnvDTE アセンブリの横にあるチェック ボックスを選択し、、 **OK**ボタン。  
  
5.  **ソリューション エクスプ ローラー**下で、**参照**のフォルダー、 **ProjectExtension**プロジェクトで、選択**EnvDTE**します。  
  
6.  **プロパティ**ウィンドウで、変更、 **Embed Interop Types**プロパティを**False**します。  
  
## <a name="define-the-new-sharepoint-project-property"></a>新しい SharePoint プロジェクトのプロパティを定義します。
 プロジェクトの拡張機能と、新しいプロジェクト プロパティの動作を定義するクラスを作成します。 新しいプロジェクトの拡張機能をクラスが実装を定義する、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>インターフェイス。 SharePoint プロジェクトの拡張機能を定義するときに、このインターフェイスを実装します。 また、追加、<xref:System.ComponentModel.Composition.ExportAttribute>クラスにします。 この属性により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を検出して読み込む、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>実装します。 渡す、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>属性のコンス トラクターを型。  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>新しい SharePoint プロジェクトのプロパティを定義するには  
  
1.  CustomProperty のコード ファイルには、次のコードを貼り付けます。  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>ソリューションをビルドする
 次に、エラーなしにコンパイルできるかどうかを確認するソリューションをビルドします。  
  
#### <a name="to-build-the-solution"></a>ソリューションをビルドするには  
  
1.  メニュー バーで、**[ビルド]** > **[ソリューションのビルド]** の順にクリックします。  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>プロジェクト プロパティの拡張機能を配置するための VSIX パッケージを作成します。
 プロジェクトの拡張機能をデプロイするのにには、VSIX パッケージを作成するのにソリューションで VSIX プロジェクトを使用します。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**、source.extension.vsixmanifest ファイルのショートカット メニューを開き、選択し、**開く**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] マニフェスト デザイナーでファイルを開きます。 表示される情報、**メタデータ**にも表示されます タブ、**拡張機能と更新**します。 すべての VSIX パッケージには、extension.vsixmanifest ファイルが必要です。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。  
  
2.  **製品名**ボックスに、入力**プロジェクトのプロパティをカスタム**します。  
  
3.  **作成者**ボックスに、入力**Contoso**します。  
  
4.  **説明**ボックスに、入力**カスタム SharePoint プロジェクト プロパティをプロジェクトにイメージ リソース フォルダーのマッピングを切り替える**します。  
  
5.  選択、**資産**、タブをクリックして、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MEFComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)します。  
  
7.  **ソース**一覧で、選択、**現在のソリューションでプロジェクトを**オプション ボタンをクリックします。  
  
8.  **プロジェクト**一覧で、選択**ProjectExtension**します。  
  
     この値は、プロジェクトでビルドしているアセンブリの名前を識別します。  
  
9. 選択**OK**を閉じる、**新しい資産の追加** ダイアログ ボックス。  
  
10. メニュー バーで、**ファイル** > **すべてを保存**を完了し、マニフェスト デザイナーを閉じます。  
  
11. メニュー バーで、**ビルド** > **ソリューションのビルド**のエラーのないプロジェクトをコンパイルできるかどうかを確認します。  
  
12. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProjectExtensionPackage**プロジェクトを選び、**ファイル エクスプ ローラーでフォルダーを開く**ボタンをクリックします。  
  
13. **ファイル エクスプ ローラー**ProjectExtensionPackage プロジェクトのビルド出力フォルダーを開きのフォルダーに ProjectExtensionPackage.vsix がという名前のファイルが含まれていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="test-the-project-property"></a>テスト プロジェクトのプロパティ
 カスタム プロジェクトのプロパティをテストする準備ができました。 デバッグおよびの実験用インスタンスで新しいプロジェクト プロパティの拡張機能をテストする最も簡単[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 このインスタンスの[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]VSIX またはその他の機能拡張プロジェクトを実行するときに作成されます。 プロジェクトをデバッグした後は、システムに拡張機能のインストールし、デバッグの通常のインスタンスでテストを続行し、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>デバッグおよび Visual Studio の実験用インスタンスで、拡張機能をテストするには  
  
1.  再起動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]管理者の資格情報と ProjectExtensionPackage ソリューションを開きます。  
  
2.  いずれかを選択して、プロジェクトのデバッグ ビルドを開始、 **F5**キーか、メニュー バーで**デバッグ** > **デバッグの開始**します。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom プロジェクト Property\1.0 に拡張をインストールしの実験用インスタンスを起動する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
3.  実験用インスタンスで[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ファーム ソリューションでは、SharePoint プロジェクトを作成し、ウィザードの他の値の既定値を使用します。  
  
    1.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
    2.  上部にある、**新しいプロジェクト** ダイアログ ボックスで、選択 **.NET Framework 3.5**で .NET Framework のバージョンの一覧。  
  
         このバージョンの機能を SharePoint ツール拡張機能が必要、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]します。  
  
    3.  下、**テンプレート**ノード、展開、 **Visual c#** または**Visual Basic**ノードで、選択、 **SharePoint**ノード、を選択し**2010**ノード。  
  
    4.  選択、 **SharePoint 2010 プロジェクト**テンプレート、し、入力**ModuleTest**として、プロジェクトの名前。  
  
4.  **ソリューション エクスプ ローラー**、選択、 **ModuleTest**プロジェクト ノード。  
  
     新しいカスタム プロパティ**マップ イメージ フォルダー**に表示されます、**プロパティ**ウィンドウで、既定値は**False**します。  
  
5.  そのプロパティの値を変更**True**します。  
  
     イメージのリソース フォルダーは、SharePoint プロジェクトに追加されます。  
  
6.  そのプロパティの値に戻して**False**します。  
  
     選択した場合、 **[はい]** ボタン、 **Images フォルダーを削除しますか?** ダイアログ ボックスで、イメージのリソース フォルダーは、SharePoint プロジェクトから削除します。  
  
7.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の実験用インスタンスを閉じます。  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクトを拡張します。](../sharepoint/extending-sharepoint-projects.md)   
 [方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換します。](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [SharePoint プロジェクト システムの拡張機能でデータを保存します。](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
