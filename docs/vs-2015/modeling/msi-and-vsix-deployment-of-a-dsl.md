---
title: MSI および VSIX 配置 DSL の |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 81b027e9834fccadcc572cad8fae4d721be9dd56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922043"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL の MSI および VSIX 配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

自分のコンピューターまたは他のコンピューターでは、ドメイン固有言語をインストールできます。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ターゲット コンピューターに既にインストールする必要があります。  
  
##  <a name="which"></a> VSIX および MSI の展開の使い分け  
 ドメイン固有言語の配置の 2 つの方法はあります。  
  
|メソッド|利点|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能)|非常に簡単にデプロイ: コピーし、実行、 **.vsix** DslPackage プロジェクトからのファイル。<br /><br /> 詳細については、次を参照してください。[をインストールすると、VSX を使用して DSL をアンインストール](#Installing)します。|  
|MSI (インストーラー ファイル)|-ユーザーを開くことを許可する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DSL のファイルをダブルクリックします。<br />-対象のコンピューターで DSL のファイルの種類のアイコンに関連付けます。<br />-DSL のファイルの種類 XSD (XML スキーマ) に関連付けます。 ファイルが読み込まれるときに警告を回避できますこの[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。<br /><br /> MSI を作成するソリューションには、セットアップ プロジェクトを追加する必要があります。<br /><br /> 詳細については、次を参照してください。 [MSI ファイルを使用して DSL を展開する](#msi)します。|  
  
##  <a name="Installing"></a> インストールして、VSX を使用して DSL をアンインストールします。  
 内からユーザーが DSL のファイルを開くときに、このメソッドでは、DSL をインストール、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が Windows エクスプ ローラーからファイルを開くことはできません。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX を使用して DSL をインストールするには  
  
1.  自分のコンピューターでは、検索、 **.vsix** DSL パッケージ プロジェクトによってビルドされたファイル。  
  
    1.  **ソリューション エクスプ ローラー**を右クリックし、 **DslPackage**プロジェクトをクリックして**Windows エクスプ ローラーでフォルダーを開く**します。  
  
    2.  ファイルを見つけます**bin\\\*\\**_プロジェクト_**します。DslPackage.vsix**  
  
2.  コピー、 **.vsix**ファイルを DSL をインストールするターゲット コンピューターにします。 自分のコンピューターでも別のコンピューターでもかまいません。  
  
    -   ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]実行時に Dsl をサポートします。 詳細については、次を参照してください。[視覚化 & Modeling SDK for Visual Studio のエディションをサポートされている](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)します。  
  
    -   ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で指定されている**DslPackage\source.extensions.manifest**します。  
  
3.  対象のコンピューターをダブルクリック、 **.vsix**ファイル。  
  
     **Visual Studio 拡張機能インストーラー** が起動され、拡張機能がインストールされます。  
  
4.  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]を起動または再起動します。  
  
5.  DSL をテストする[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DSL 用に定義した拡張子を持つ新しいファイルを作成します。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX を使用して、インストールされている DSL をアンインストールするには  
  
1. **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
2. **[インストール済みの拡張機能]** を展開します。  
  
3. クリックして、DSL が定義されている拡張機能の選択**アンインストール**します。  
  
   拡張機能の障害が原因で読み込みが失敗し、エラー ウィンドウにレポートが生成されることがまれにありますが、それは拡張機能マネージャーには表示されません。 その場合は、以下の場所からファイルを削除して、拡張機能を削除します。  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a> DSL の MSI を展開します。  
 DSL の MSI (Windows インストーラー) ファイルを定義すると、ユーザーが Windows エクスプ ローラーから DSL のファイルを開くことができます。 アイコンと簡単な説明も、ファイル名拡張子を関連付けることができます。 さらに、MSI は、DSL のファイルの検証に使用できる XSD をインストールできます。 する場合は、同時にインストールされる MSI にその他のコンポーネントを追加できます。  
  
 MSI ファイルとその他のデプロイ オプションの詳細については、次を参照してください。[アプリケーションの配置、サービス、およびコンポーネント](../deployment/deploying-applications-services-and-components.md)します。  
  
 MSI を作成するにセットアップ プロジェクトを追加、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ソリューション。 セットアップ プロジェクトを作成する最も簡単な方法からダウンロードできます CreateMsiSetupProject.tt テンプレートを使用して、 [VMSDK サイト](http://go.microsoft.com/fwlink/?LinkID=186128)します。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>DSL の MSI を展開するには  
  
1. 設定`InstalledByMsi`拡張機能マニフェスト。 これにより、VSX 防止インストールされ、を除き、MSI をアンインストールできます。 これは、場合は、MSI にその他のコンポーネントを含めるが重要です。  
  
   1.  DslPackage\source.extension.tt を開く  
  
   2.  前に、次の行を挿入`<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. 作成するか、Windows エクスプ ローラーで DSL を表すアイコンを編集します。 たとえば、編集**DslPackage\Resources\File.ico**  
  
3. DSL の次の属性が正しいことを確認します。  
  
   -   DSL エクスプ ローラーでルート ノードをクリックし、[プロパティ] ウィンドウで確認します。  
  
       -   説明  
  
       -   Version  
  
   -   をクリックして、**エディター**ノード プロパティ ウィンドウで次のようにクリックします。**アイコン**します。 アイコン ファイルを参照する値を設定**DslPackage\Resources**など**File.ico**  
  
   -   **ビルド**] メニューの [open **Configuration Manager**などのビルドする構成を選択します**リリース**または**デバッグ**.  
  
4. 移動して[Visualization and Modeling SDK のホーム ページ](http://go.microsoft.com/fwlink/?LinkID=186128)との間、**ダウンロード** タブで、ダウンロード**CreateMsiSetupProject.tt**します。  
  
5. 追加**CreateMsiSetupProject.tt**を Dsl プロジェクトにします。  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] という名前のファイルが作成されます**CreateMsiSetupProject.vdproj**します。  
  
6. Windows エクスプローラで、コピー Dsl\\\*.vdproj を新しいフォルダーにセットアップをという名前です。  
  
    (する場合は、今すぐから除外できます CreateMsiSetupProject.tt Dsl プロジェクト。)  
  
7. **ソリューション エクスプ ローラー**、追加**セットアップ\\\*.vdproj**として既存のプロジェクト。  
  
8. **プロジェクト** メニューのをクリックして**プロジェクトの依存関係**します。  
  
    **プロジェクトの依存関係** ダイアログ ボックスで、セットアップ プロジェクトを選択します。  
  
    次に、ボックスをオン**DslPackage**します。  
  
9. ソリューションをリビルドします。  
  
10. Windows エクスプ ローラーでは、セットアップ プロジェクトでビルドした MSI ファイルを見つけます。  
  
     DSL をインストールするコンピューターに MSI ファイルをコピーします。 MSI ファイルをダブルクリックします。 インストーラーを実行します。  
  
11. 対象のコンピューターでは、DSL のファイル拡張子を持つ新しいファイルを作成します。 確認します。  
  
    -   Windows エクスプ ローラーのリスト ビューで、ファイルはアイコンと定義した説明が表示されます。  
  
    -   ファイルをダブルクリックすると、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が開始され、DSL エディターで、DSL のファイルを開きます。  
  
    場合は、テキスト テンプレートを使用する代わりに、手動でセットアップ プロジェクトを作成できます。 この手順を含むチュートリアルの第 5 章を参照してください、 [Visualization and Modeling SDK ラボ](http://go.microsoft.com/fwlink/?LinkId=208878)します。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI からインストールされている DSL をアンインストールするには  
  
1.  Windows を開き、**プログラムと機能**コントロール パネル。  
  
2.  DSL をアンインストールします。  
  
3.  Visual Studio を再起動します。



