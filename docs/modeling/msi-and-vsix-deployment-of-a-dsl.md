---
title: "MSI と、DSL の VSIX 配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: dafee91f26cf45d780f1b222d8daf5977980a3f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL の MSI および VSIX 配置
自分のコンピューター上またはその他のコンピューター上、ドメイン固有言語をインストールすることができます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ターゲット コンピューターに既にインストールする必要があります。  
  
##  <a name="which"></a>VSIX および MSI の展開の使い分け  
 ドメイン固有言語を展開する次の 2 つの方法はあります。  
  
|メソッド|利点|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能)|非常に簡単に展開: コピーし、実行、 **.vsix** DslPackage プロジェクトからのファイルです。<br /><br /> 詳細については、次を参照してください。[をインストールすると、VSX を使用して、DSL をアンインストール](#Installing)です。|  
|MSI (インストーラー ファイル)|-を開くには、ユーザーは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DSL ファイルをダブルクリックします。<br />-対象のコンピューターでの DSL ファイルの種類のアイコンに関連付けます。<br />-DSL ファイルの種類 XSD (XML スキーマ) に関連付けます。 ファイルが読み込まれるときに警告を回避できますこの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。<br /><br /> セットアップ プロジェクトは、MSI を作成するようにソリューションを追加する必要があります。<br /><br /> 詳細については、次を参照してください。 [DSL を展開する MSI ファイルを使用して](#msi)です。|  
  
##  <a name="Installing"></a>インストールして、VSX を使用して、DSL のアンインストール  
 ユーザーが内から DSL ファイルを開くことができます、DSL は、インストールすると、このメソッドによって[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]は Windows エクスプ ローラーからファイルを開くことはできません。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>DSL を VSX を使用してインストールするには  
  
1.  自分のコンピューターでは、検索、 **.vsix** DSL パッケージ プロジェクトによってビルドされたファイルです。  
  
    1.  **ソリューション エクスプ ローラー**を右クリックし、 **DslPackage**プロジェクトをクリックして**Windows エクスプ ローラーでフォルダーを開く**です。  
  
    2.  ファイルを探します**bin\\\*\\***プロジェクト***です。DslPackage.vsix**  
  
2.  コピー、 **.vsix** DSL をインストールするターゲット コンピューターへのファイルです。 自分のコンピューターでも別のコンピューターでもかまいません。  
  
    -   対象のコンピューターには、いずれかのエディションが必要[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]実行時に、Dsl をサポートしています。 詳細については、次を参照してください。 [Visual Studio のエディションの視覚化およびモデリング SDK のサポートされている](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)です。  
  
    -   対象のコンピューターには、いずれかのエディションが必要[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]で指定された**DslPackage\source.extensions.manifest**です。  
  
3.  ターゲット コンピューターをダブルクリックして、 **.vsix**ファイル。  
  
     **Visual Studio 拡張機能インストーラー** が起動され、拡張機能がインストールされます。  
  
4.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を起動または再起動します。  
  
5.  DSL をテストする使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL 用に定義した拡張子を持つ新しいファイルを作成します。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>DSL VSX を使用してインストールされたをアンインストールするには  
  
1.  **ツール** メニューのをクリックして**拡張機能マネージャー**です。  
  
2.  **[インストール済みの拡張機能]**を展開します。  
  
3.  クリックして、DSL が定義されている拡張機能の選択**アンインストール**です。  
  
 拡張機能の障害が原因で読み込みが失敗し、エラー ウィンドウにレポートが生成されることがまれにありますが、それは拡張機能マネージャーには表示されません。 その場合は、以下の場所からファイルを削除して、拡張機能を削除します。  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a>MSI の DSL の展開  
 MSI (Windows インストーラー) ファイルを定義すると、dsl には、ユーザーが Windows エクスプ ローラーから DSL ファイルを開くことができます。 アイコンと短い説明も、ファイル名拡張子を持つ関連付けることができます。 さらに、MSI は、DSL ファイルの検証に使用できる XSD をインストールできます。 する場合は、同時にインストールされる MSI に他のコンポーネントを追加できます。  
  
 MSI ファイルとその他の展開オプションの詳細については、次を参照してください。[アプリケーション、サービス、および配置コンポーネント](../deployment/deploying-applications-services-and-components.md)です。  
  
 MSI をビルドするにセットアップ プロジェクトを追加する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションです。 セットアップ プロジェクトを作成する最も簡単な方法からダウンロードできる CreateMsiSetupProject.tt テンプレートを使用する、 [VMSDK サイト](http://go.microsoft.com/fwlink/?LinkID=186128)です。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>DSL MSI でを展開するには  
  
1.  設定`InstalledByMsi`拡張機能マニフェストでします。 これにより、VSX 防止インストールされ、を除き、MSI をアンインストールできます。 これは、msi ファイル内の他のコンポーネントを含める場合に重要です。  
  
    1.  DslPackage\source.extension.tt を開く  
  
    2.  前に、次の行を挿入`<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  作成または編集をエクスプ ローラーで、DSL を表すアイコン。 たとえば、編集**DslPackage\Resources\File.ico**  
  
3.  DSL の次の属性が正しいことを確認します。  
  
    -   DSL のエクスプ ローラーで、ルート ノードをクリックし、[プロパティ] ウィンドウで確認します。  
  
        -   説明  
  
        -   Version  
  
    -   クリックして、**エディター**ノードのプロパティ ウィンドウで、をクリック**アイコン**です。 アイコン ファイルで参照する値を設定**DslPackage\Resources**など**File.ico**  
  
    -   **ビルド**] メニューの [開いている**Configuration Manager**、構成などをビルドするを選択して**リリース**または**デバッグ**.  
  
4.  移動して[Visualization and Modeling SDK のホーム ページ](http://go.microsoft.com/fwlink/?LinkID=186128)との間、**ダウンロード** タブで、ダウンロード**CreateMsiSetupProject.tt**です。  
  
5.  追加**CreateMsiSetupProject.tt** Dsl プロジェクトにします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前のファイルが作成されます**CreateMsiSetupProject.vdproj**です。  
  
6.  Windows エクスプローラで、コピー Dsl\\*.vdproj を新しいフォルダーにセットアップをという名前です。  
  
     (する場合は、今すぐから除外できます CreateMsiSetupProject.tt Dsl プロジェクトです。)  
  
7.  **ソリューション エクスプ ローラー**、追加**セットアップ\\\*.vdproj**として既存のプロジェクトです。  
  
8.  **プロジェクト** メニューのをクリックして**プロジェクトの依存関係**です。  
  
     **プロジェクトの依存関係** ダイアログ ボックスで、セットアップ プロジェクトを選択します。  
  
     次に、ボックスをオン**DslPackage**です。  
  
9. ソリューションをリビルドします。  
  
10. Windows エクスプ ローラーで、セットアップ プロジェクトでビルドした MSI ファイルを見つけます。  
  
     MSI ファイルを DSL をインストールするコンピューターにコピーします。 MSI ファイルをダブルクリックします。 インストーラーを実行します。  
  
11. ターゲット コンピューターでは、DSL のファイル拡張子を持つ新しいファイルを作成します。 次のことを確認します。  
  
    -   Windows エクスプ ローラーのリスト ビュー ファイルは、アイコン、定義した説明が表示されます。  
  
    -   ファイルをダブルクリックすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開始、および DSL ファイルを DSL エディターで開きます。  
  
 場合は、テキスト テンプレートを使用する代わりに、手動でセットアップ プロジェクトを作成します。 この手順を含むチュートリアルの第 5 章を参照してください、[視覚化およびモデリング SDK ラボ](http://go.microsoft.com/fwlink/?LinkId=208878)です。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI からインストールされた DSL をアンインストールするには  
  
1.  Windows では、開く、**プログラムと機能**コントロール パネルの します。  
  
2.  DSL をアンインストールします。  
  
3.  Visual Studio を再起動します。