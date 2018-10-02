---
title: DSL の MSI および VSIX 配置
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: c8a7c88c0c1808b5155ada9d46cfbdad9edd5cf5
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859355"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL の MSI および VSIX 配置
自分のコンピューターまたは他のコンピューターでは、ドメイン固有言語をインストールできます。 Visual Studio は、ターゲット コンピューターに既にインストールする必要があります。

## <a name="which"></a> VSIX および MSI の展開の使い分け
 ドメイン固有言語の配置の 2 つの方法はあります。

|メソッド|利点|
|------------|--------------|
|VSX (Visual Studio 拡張機能)|非常に簡単にデプロイ: コピーし、実行、 **.vsix** DslPackage プロジェクトからのファイル。<br /><br /> 詳細については、次を参照してください。[をインストールすると、VSX を使用して DSL をアンインストール](#Installing)します。|
|MSI (インストーラー ファイル)|-DSL のファイルをダブルクリックして Visual Studio を開くことを許可します。<br />-対象のコンピューターで DSL のファイルの種類のアイコンに関連付けます。<br />-DSL のファイルの種類 XSD (XML スキーマ) に関連付けます。 これにより、ファイルが Visual Studio に読み込まれると、警告を回避できます。<br /><br /> MSI を作成するソリューションには、セットアップ プロジェクトを追加する必要があります。<br /><br /> 詳細については、次を参照してください。 [MSI ファイルを使用して DSL を展開する](#msi)します。|

## <a name="Installing"></a> インストールして、VSX を使用して DSL をアンインストールします。
 このメソッドでは、DSL をインストール、ユーザーは、Visual Studio 内から DSL ファイルを開くことができますが、Windows エクスプ ローラーからファイルを開くことができません。

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX を使用して DSL をインストールするには

1.  自分のコンピューターでは、検索、 **.vsix** DSL パッケージ プロジェクトによってビルドされたファイル。

    1.  **ソリューション エクスプ ローラー**を右クリックし、 **DslPackage**プロジェクトをクリックして**Windows エクスプ ローラーでフォルダーを開く**します。

    2.  ファイルを見つけます**bin\\\*\\**_プロジェクト_**します。DslPackage.vsix**

2.  コピー、 **.vsix**ファイルを DSL をインストールするターゲット コンピューターにします。 自分のコンピューターでも別のコンピューターでもかまいません。

    -   ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]実行時に Dsl をサポートします。 詳細については、次を参照してください。[視覚化 & Modeling SDK for Visual Studio のエディションをサポートされている](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)します。

    -   ターゲット コンピューターで指定された Visual Studio のエディションのいずれかが必要**DslPackage\source.extensions.manifest**します。

3.  対象のコンピューターをダブルクリック、 **.vsix**ファイル。

     **Visual Studio 拡張機能インストーラー** が起動され、拡張機能がインストールされます。

4.  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を起動または再起動します。

5.  DSL をテストするには、Visual Studio を使用して DSL 用に定義した拡張子を持つ新しいファイルを作成します。

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX を使用して、インストールされている DSL をアンインストールするには

1.  **ツール** メニューのをクリックして**拡張機能マネージャー**します。

2.  **[インストール済みの拡張機能]** を展開します。

3.  クリックして、DSL が定義されている拡張機能の選択**アンインストール**します。

 拡張機能の障害が原因で読み込みが失敗し、エラー ウィンドウにレポートが生成されることがまれにありますが、それは拡張機能マネージャーには表示されません。 その場合は、以下の場所からファイルを削除して、拡張機能を削除します。

 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a> DSL の MSI を展開します。
 DSL の MSI (Windows インストーラー) ファイルを定義すると、ユーザーが Windows エクスプ ローラーから DSL のファイルを開くことができます。 アイコンと簡単な説明も、ファイル名拡張子を関連付けることができます。 さらに、MSI は、DSL のファイルの検証に使用できる XSD をインストールできます。 する場合は、同時にインストールされる MSI にその他のコンポーネントを追加できます。

 MSI ファイルとその他のデプロイ オプションの詳細については、次を参照してください。[アプリケーションの配置、サービス、およびコンポーネント](../deployment/deploying-applications-services-and-components.md)します。

 MSI を作成するには、Visual Studio ソリューションにセットアップ プロジェクトを追加します。 セットアップ プロジェクトを作成する最も簡単な方法からダウンロードできます CreateMsiSetupProject.tt テンプレートを使用して、 [VMSDK サイト](http://go.microsoft.com/fwlink/?LinkID=186128)します。

#### <a name="to-deploy-a-dsl-in-an-msi"></a>DSL の MSI を展開するには

1.  設定`InstalledByMsi`拡張機能マニフェスト。 これにより、VSX 防止インストールされ、を除き、MSI をアンインストールできます。 これは、場合は、MSI にその他のコンポーネントを含めるが重要です。

    1.  DslPackage\source.extension.tt を開く

    2.  前に、次の行を挿入`<SupportedProducts>`:

        ```xml
        <InstalledByMsi>true</InstalledByMsi>
        ```

2.  作成するか、Windows エクスプ ローラーで DSL を表すアイコンを編集します。 たとえば、編集**DslPackage\Resources\File.ico**

3.  DSL の次の属性が正しいことを確認します。

    -   DSL エクスプ ローラーでルート ノードをクリックし、[プロパティ] ウィンドウで確認します。

        -   説明

        -   Version

    -   をクリックして、**エディター**ノード プロパティ ウィンドウで次のようにクリックします。**アイコン**します。 アイコン ファイルを参照する値を設定**DslPackage\Resources**など**File.ico**

    -   **ビルド**] メニューの [open **Configuration Manager**などのビルドする構成を選択します**リリース**または**デバッグ**.

4.  移動して[Visualization and Modeling SDK のホーム ページ](http://go.microsoft.com/fwlink/?LinkID=186128)との間、**ダウンロード** タブで、ダウンロード**CreateMsiSetupProject.tt**します。

5.  追加**CreateMsiSetupProject.tt**を Dsl プロジェクトにします。

     Visual Studio はという名前のファイルを作成**CreateMsiSetupProject.vdproj**します。

6.  Windows エクスプローラで、コピー Dsl\\\*.vdproj を新しいフォルダーにセットアップをという名前です。

     (する場合は、今すぐから除外できます CreateMsiSetupProject.tt Dsl プロジェクト。)

7.  **ソリューション エクスプ ローラー**、追加**セットアップ\\\*.vdproj**として既存のプロジェクト。

8.  **プロジェクト** メニューのをクリックして**プロジェクトの依存関係**します。

     **プロジェクトの依存関係** ダイアログ ボックスで、セットアップ プロジェクトを選択します。

     次に、ボックスをオン**DslPackage**します。

9. ソリューションをリビルドします。

10. Windows エクスプ ローラーでは、セットアップ プロジェクトでビルドした MSI ファイルを見つけます。

     DSL をインストールするコンピューターに MSI ファイルをコピーします。 MSI ファイルをダブルクリックします。 インストーラーを実行します。

11. 対象のコンピューターでは、DSL のファイル拡張子を持つ新しいファイルを作成します。 確認します。

    -   Windows エクスプ ローラーのリスト ビューで、ファイルはアイコンと定義した説明が表示されます。

    -   ときにファイル、Visual Studio の起動 をダブルクリックし、DSL のエディターで、DSL のファイルを開きます。

 場合は、テキスト テンプレートを使用する代わりに、手動でセットアップ プロジェクトを作成できます。 この手順を含むチュートリアルの第 5 章を参照してください、 [Visualization and Modeling SDK ラボ](http://go.microsoft.com/fwlink/?LinkId=208878)します。

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI からインストールされている DSL をアンインストールするには

1.  Windows を開き、**プログラムと機能**コントロール パネル。

2.  DSL をアンインストールします。

3.  Visual Studio を再起動します。