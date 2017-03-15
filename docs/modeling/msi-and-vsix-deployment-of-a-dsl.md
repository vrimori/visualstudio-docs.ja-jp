---
title: "MSI および VSIX 配置 DSL の |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL の MSI および VSIX 配置
自分のコンピューターまたは他のコンピューターは、ドメイン固有言語をインストールできます。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ターゲット コンピューターにインストールされている必要があります。  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>VSIX および MSI の展開の使い分け  
 ドメイン固有言語の展開の&2; つの方法はあります。  
  
|メソッド|利点|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能)|非常に簡単に展開します。 コピーし、実行、 **.vsix** DslPackage プロジェクトからファイルです。<br /><br /> 詳細については、次を参照してください。[をインストールすると、VSX を使用して DSL をアンインストールするには](#Installing)です。|  
|MSI (インストーラー ファイル)|-を開くには、ユーザーは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DSL のファイルをダブルクリックします。<br />-対象のコンピュータで DSL のファイルの種類のアイコンに関連付けます。<br />-DSL のファイルの種類 XSD (XML スキーマ) に関連付けます。 ファイルが読み込まれると、警告を回避できます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。<br /><br /> セットアップ プロジェクトは、MSI を作成するためのソリューションに追加する必要があります。<br /><br /> 詳細については、次を参照してください。 [MSI ファイルを使用して DSL を展開する](#msi)です。|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>インストールして、VSX を使用して DSL をアンインストールするには  
 このメソッドで、DSL をインストールすると、ユーザーが内から DSL のファイルを開くことができます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が Windows エクスプ ローラーからファイルを開くことはできません。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX を使用して DSL をインストールするには  
  
1.  自分のコンピューターでは、検索、 **.vsix** DSL パッケージ プロジェクトによってビルドされたファイルです。  
  
    1.  **ソリューション エクスプ ローラー**を右クリックし、 **DslPackage** [プロジェクト] をクリックして**Windows エクスプ ローラーでフォルダーを開く**します。  
  
    2.  Locate the file **bin\\\*\\***YourProject***.DslPackage.vsix**  
  
2.  コピー、 **.vsix** DSL をインストールするターゲット コンピューターへのファイルです。 自分のコンピューターでも別のコンピューターでもかまいません。  
  
    -   ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]実行時に Dsl をサポートします。 詳細については、次を参照してください。[視覚化 >/documents/report1.rdl」のモデリング SDK の Visual Studio のエディションをサポートされている](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)します。  
  
    -   ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]で指定されている**DslPackage\source.extensions.manifest**します。  
  
3.  対象のコンピューターをダブルクリックして、 **.vsix**ファイルです。  
  
     **Visual Studio 拡張機能インストーラー** が起動され、拡張機能がインストールされます。  
  
4.  
          [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を起動または再起動します。  
  
5.  DSL をテストする使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL に対して定義されている拡張子を持つ新しいファイルを作成します。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX を使用して、インストールされている DSL をアンインストールするには  
  
1.  **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
2.  **[インストール済みの拡張機能]**を展開します。  
  
3.  クリックして、DSL が定義されている拡張機能を選択して**アンインストール**します。  
  
 拡張機能の障害が原因で読み込みが失敗し、エラー ウィンドウにレポートが生成されることがまれにありますが、それは拡張機能マネージャーには表示されません。 その場合は、以下の場所からファイルを削除して、拡張機能を削除します。  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>MSI の DSL を配置します。  
 DSL の MSI (Windows インストーラー) ファイルを定義して、ユーザーが Windows エクスプ ローラーから DSL のファイルを開くことを許可できます。 ファイル名の拡張子で、アイコンと簡単な説明を関連付けることができます。 さらに、MSI は、DSL のファイルの検証に使用できる XSD をインストールできます。 する場合は、同時にインストールされる MSI に他のコンポーネントを追加できます。  
  
 MSI ファイルとその他の展開オプションの詳細については、次を参照してください。[アプリケーションの配置、サービス、およびコンポーネント](../deployment/deploying-applications-services-and-components.md)します。  
  
 MSI をビルドするをセットアップ プロジェクトを追加する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションです。 セットアップ プロジェクトを作成する最も簡単な方法からダウンロードできます CreateMsiSetupProject.tt テンプレートを使用する、 [VMSDK サイト](http://go.microsoft.com/fwlink/?LinkID=186128)します。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI の DSL を展開するには  
  
1.  設定`InstalledByMsi`拡張機能マニフェストにします。 これは、ため、VSX がインストールされ、msi ファイルを除くアンインストールします。 これは、場合は、MSI に他のコンポーネントを含めるが重要です。  
  
    1.  DslPackage\source.extension.tt を開く  
  
    2.  前に、次の行を挿入`<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  作成または編集を Windows エクスプ ローラーで、DSL を表すアイコン。 たとえば、編集**DslPackage\Resources\File.ico**  
  
3.  DSL の次の属性が正しいことを確認します。  
  
    -   DSL エクスプ ローラーで、ルート ノードをクリックし、[プロパティ] ウィンドウで確認します。  
  
        -   説明  
  
        -   バージョン  
  
    -   クリックして、**エディター**ノード プロパティ ウィンドウでをクリック**アイコン**します。 アイコン ファイルで参照する値を設定**DslPackage\Resources**など**File.ico**  
  
    -   **ビルド**] メニューの [開く**Configuration Manager**などをビルドする構成を選択**リリース**または**デバッグ**します。  
  
4.  移動して[Visualization and Modeling SDK のホーム ページ](http://go.microsoft.com/fwlink/?LinkID=186128)との間、**ダウンロード** タブで、ダウンロード**CreateMsiSetupProject.tt**します。  
  
5.  追加**CreateMsiSetupProject.tt**を Dsl プロジェクトにします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前のファイルを作成**CreateMsiSetupProject.vdproj**します。  
  
6.  Windows エクスプ ローラーで Dsl をコピー\\*.vdproj 新しいフォルダーにセットアップをという名前です。  
  
     (する場合は、今すぐから除外できます CreateMsiSetupProject.tt Dsl プロジェクトです。)  
  
7.  **ソリューション エクスプ ローラー**、追加**セットアップ\\\*.vdproj**既存のプロジェクトとします。  
  
8.  **プロジェクト** メニューのをクリックして**プロジェクトの依存関係**します。  
  
     **プロジェクトの依存関係** ダイアログ ボックスで、セットアップ プロジェクトを選択します。  
  
     次のボックスをオン**DslPackage**します。  
  
9. ソリューションをリビルドします。  
  
10. Windows エクスプ ローラーでは、セットアップ プロジェクトでビルドした MSI ファイルを見つけます。  
  
     MSI ファイルを DSL をインストールするコンピューターにコピーします。 MSI ファイルをダブルクリックします。 インストーラーを実行します。  
  
11. ターゲット コンピューターでは、DSL のファイル拡張子を持つ新しいファイルを作成します。 次のことを確認します。  
  
    -   Windows エクスプ ローラー ボックスの一覧表示、ファイルをアイコンと定義した説明が表示されます。  
  
    -   ファイルをダブルクリックすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が開始され、DSL のエディターで、DSL のファイルを開きます。  
  
 を行う場合は、テキスト テンプレートを使用する代わりにセットアップ プロジェクトを手動で、作成することができます。 この手順を含むチュートリアルの第 5 章を参照してください、[視覚化およびモデリング SDK ラボ](http://go.microsoft.com/fwlink/?LinkId=208878)します。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI からインストールされている DSL をアンインストールするには  
  
1.  Windows では、開く、**プログラムと機能**コントロール パネルです。  
  
2.  DSL をアンインストールします。  
  
3.  Visual Studio を再起動します。
