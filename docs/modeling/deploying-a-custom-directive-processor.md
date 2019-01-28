---
title: カスタム ディレクティブ プロセッサの配置
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6563691022fdd1694af69e872aa0d37803c2191c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956169"
---
# <a name="deploying-a-custom-directive-processor"></a>カスタム ディレクティブ プロセッサの配置

Visual Studio でカスタム ディレクティブ プロセッサを使用して、任意のコンピューターで、このトピックで説明する方法のいずれかによって登録する必要があります。

次の方法があります。

-   [Visual Studio 拡張機能](../extensibility/shipping-visual-studio-extensions.md)します。 これを使用すると、ディレクティブ プロセッサを自分のコンピューターと他のコンピューターの両方でインストールおよびアンインストールできます。 通常は、他の機能も同じ VSIX にパッケージ化します。

-   [VSPackage](../extensibility/internals/vspackages.md)します。 ディレクティブ プロセッサ以外の機能も含む VSPackage を定義する場合は、ディレクティブ プロセッサの便利な登録方法を利用できます。

-   レジストリ キーを設定する。 この方法では、ディレクティブ プロセッサのレジストリ エントリを追加します。

Visual Studio または MSBuild でテキスト テンプレートを変換する場合にのみ、これらのメソッドのいずれかを使用する必要があります。 独自のアプリケーションのカスタム ホストを使用する場合は、そのカスタム ホストを通じて各ディレクティブのディレクティブ プロセッサを探します。

## <a name="deploying-a-directive-processor-in-a-vsix"></a>VSIX でのディレクティブ プロセッサの配置

カスタム ディレクティブ プロセッサを追加することができます、 [Visual Studio Extension (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md)します。

 .vsix ファイルに次の 2 つのアイテムが格納されていることを確認する必要があります。

-   カスタム ディレクティブ プロセッサ クラスを含むアセンブリ (.dll)。

-   ディレクティブ プロセッサを登録する .pkgdef ファイル。 このファイルのルート名は、アセンブリと同じにする必要があります。 たとえば、アセンブリ ファイル名が CDP.dll のときは、CDP.pkgdef にします。

.vsix ファイルのコンテンツを確認または変更するには、そのファイル名拡張子を .zip に変更してから開きます。 コンテンツの編集が終わったら、ファイル名拡張子を .vsix に戻します。

.vsix ファイルはいくつかの方法で作成できます。 次の手順では、そのうちの 1 つについて説明します。

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>VSIX プロジェクトでカスタム ディレクティブ プロセッサを作成するには

1.  Visual Studio で VSIX プロジェクトを作成します。

    -   **新しいプロジェクト** ダイアログ ボックスで、展開**Visual Basic**または**Visual c#** の順に展開**Extensibility**します。 クリックして**VSIX プロジェクト**します。

2.  **Source.extension.vsixmanifest**コンテンツの種類を設定し、サポートされているエディションです。

    1.  Vsix マニフェスト エディターで、**資産** タブで、選択**新規**し、新しい項目のプロパティを設定します。

         **コンテンツの種類** = **VSPackage**

         **プロジェクトをソース** = \<*現在のプロジェクト*>

    2.  をクリックして**選択されたエディション**ディレクティブ プロセッサを使用できるようにインストールの種類を確認します。

3.  .pkgdef ファイルを追加し、そのプロパティが VSIX に含まれるように設定します。

    1.  テキスト ファイルを作成し、名前\< *assemblyName*> .pkgdef します。

         \<*assemblyName*> は通常、プロジェクトの名前と同じです。

    2.  ソリューション エクスプローラーでこのファイルを選択し、そのプロパティを次のように設定します。

         **ビルド アクション** = **コンテンツ**

         **出力ディレクトリにコピー** = **常にコピーします。**

         **VSIX に含める** = **は True。**

    3.  VSIX の名前を設定し、ID が一意であることを確認します。

4.  次のテキストを .pkgdef ファイルに追加します。

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     名前 (`CustomDirectiveProcessorName`、`NamespaceName`、`ClassName`、`AssemblyName`) を独自の名前に置き換えます。

5.  以下の参照をプロジェクトに追加します。

    -   **Microsoft.VisualStudio.TextTemplating.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**

6.  カスタム ディレクティブ プロセッサ クラスをプロジェクトに追加します。

     これは、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> または <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> を実装する必要のあるパブリック クラスです。

#### <a name="to-install-the-custom-directive-processor"></a>カスタム ディレクティブ プロセッサをインストールするには

1.  Windows エクスプ ローラーで、ビルド ディレクトリ (通常は bin \debug または bin \release) を開きます。

2.  別のコンピューターにディレクティブ プロセッサをインストールする場合は、そのコンピューターに .vsix ファイルをコピーします。

3.  .vsix ファイルをダブルクリックします。 Visual Studio 拡張機能インストーラーが表示されます。

4.  Visual Studio を再起動します。 これで、カスタム ディレクティブ プロセッサを参照するディレクティブを含むテキスト テンプレートを実行できるようになりました。 各ディレクティブの形式は次のとおりです。

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>カスタム ディレクティブ プロセッサをアンインストールするか、一時的に無効にするには

1.  Visual Studio で**ツール** メニューのをクリックして**拡張機能マネージャー**します。

2.  ディレクティブ プロセッサを含む VSIX を選択し、クリックして**アンインストール**または**を無効にする**します。

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX に含まれるディレクティブ プロセッサのトラブルシューティング
 ディレクティブ プロセッサが機能しない場合は、次のヒントを参考にしてください。

-   カスタム ディレクティブで指定するプロセッサ名は、.pkgdef ファイルで指定した `CustomDirectiveProcessorName` と一致している必要があります。

-   `IsDirectiveSupported` メソッドは、`true` の名前が渡されたときに `CustomDirective` を返す必要があります。

-   拡張機能マネージャーでは、拡張機能が表示されない、システムでは、インストールを許可がない場合は、削除、拡張機能から **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .

-   .vsix ファイルを開き、そのコンテンツを調べます。 .vsix ファイルを開くには、ファイル名拡張子を .zip に変更します。 このファイルに .dll、.pkgdef、および extension.vsixmanifest の各ファイルが含まれていることを確認します。 extension.vsixmanifest ファイルでは、SupportedProducts ノードに適切なリストが含まれ、なおかつ Content ノードに VsPackage ノードが含まれている必要があります。

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>VSPackage でのディレクティブ プロセッサの配置
 ディレクティブ プロセッサが GAC にインストールされる VSPackage に含まれている場合は、システムで .pkgdef ファイルを自動的に生成できます。

 次の属性をパッケージ クラスに配置します。

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
>  この属性は、ディレクティブ プロセッサ クラスではなくパッケージ クラスに配置してください。

 .pkgdef ファイルは、プロジェクトをビルドしたときに生成されます。 VSPackage をインストールすると、.pkgdef ファイルにディレクティブ プロセッサが登録されます。

 .pkgdef ファイルがビルド フォルダー (通常は bin\Debug か bin\Release) に表示されることを確認します。 このフォルダーに表示されない場合は、テキスト エディターで .csproj ファイルを開き、`<GeneratePkgDefFile>false</GeneratePkgDefFile>` ノードを削除します。

 詳細については、「 [VSPackages](../extensibility/internals/vspackages.md)」を参照してください。

## <a name="setting-a-registry-key"></a>レジストリ キーの設定
 これは、カスタム ディレクティブ プロセッサをインストールする方法としては、最も優先順位の低い方法です。 この方法では、ディレクティブ プロセッサを簡単に有効化および無効化できないうえに、ディレクティブ プロセッサを他のユーザーに配布することもできません。

> [!CAUTION]
>  レジストリを誤って編集すると、システムに重大な障害をもたらす可能性があります。 レジストリを変更する前に、コンピューター上の重要なデータはすべてバックアップしてください。

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>レジストリ キーを設定してディレクティブ プロセッサを登録するには

1. `regedit` を実行します。

2. レジストリ エディターで、次のキーに移動します。

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**

    Visual Studio の実験的なバージョンでディレクティブ プロセッサをインストールする場合は、「11.0」後"Exp"を挿入します。

3. ディレクティブ プロセッサ クラスと同じ名前のレジストリ キーを追加します。

   -   レジストリ ツリー内を右クリックし、 **DirectiveProcessors**に**新規**、 をクリックし、**キー**します。

4. 新しいノードで、クラスとコードベース、またはクラスとアセンブリの文字列値を次の表に従って追加します。

   1.  作成したノードを右クリックし、[**新規**、] をクリックし、**文字列値**します。

   2.  値の名前を編集します。

   3.  名前をダブルクリックし、データを編集します。

   カスタム ディレクティブ プロセッサが GAC 内にない場合は、レジストリ サブキーを次の表に従って設定します。

|名前|型|データ|
|-|-|-|
|(既定)|REG_SZ|(値が設定されていません)|
|クラス|REG_SZ|**\<Namespace 名 >。\<クラス名 >**|
|CodeBase|REG_SZ|**\<パス >\\< アセンブリ名\>**|

 アセンブリが GAC に含まれている場合は、レジストリ サブキーを次の表に従って設定します。

|名前|型|データ|
|-|-|-|
|(既定)|REG_SZ|(値が設定されていません)|
|クラス|REG_SZ|\<**完全修飾クラス名**>|
|Assembly|REG_SZ|\<**GAC にアセンブリ名**>|

## <a name="see-also"></a>関連項目

- [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)