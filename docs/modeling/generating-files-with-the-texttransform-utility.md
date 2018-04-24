---
title: Visual Studio で TextTransform ユーティリティを使用してファイルを生成します。
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 065d9e23a8ae8b5e328786bb195d191df1388abb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform ユーティリティを使用してファイルを生成します。

TextTransform.exe は、テキスト テンプレートを変換するのに使用できるコマンド ライン ツールです。 TextTransform.exe を呼び出すときに、引数として、テキスト テンプレート ファイルの名前を指定します。 TextTransform.exe は、テキスト変換エンジンを呼び出し、テキスト テンプレートを処理します。 TextTransform.exe は通常、スクリプトから呼び出されます。 ただし、これは通常必要ありません、テキスト変換を実行するには、Visual Studio で、または、ビルド処理のためです。

> [!NOTE]
> ビルド プロセスの一環として、テキスト変換を実行する場合は、MSBuild テキスト変換タスクを使用することを検討します。 詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)です。 ためのコンピューターで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]がインストールされているアプリケーションを記述することもできます。 または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートを変換できる拡張機能です。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)です。

 TextTransform.exe は、次のディレクトリにあります。

 **\Program files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional edition、または

 **\Program files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 Enterprise エディションです。

Visual Studio の以前のバージョンで、次の場所にファイルが見つかりました。

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

ここで {のバージョン} は、インストールされている以前のバージョンに依存します。

## <a name="syntax"></a>構文

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>パラメーター

|**引数**|**説明**|
|------------------|---------------------|
|`templateName`|変換するテンプレート ファイルの名前を識別します。|

|**オプション**|**説明**|
|----------------|---------------------|
|**-out** \<filename>|変換の出力の書き込み先となるファイル。|
|**-r** \<assembly>|アセンブリをコンパイルすると、テキスト テンプレートを実行するために使用します。|
|**-u** \<namespace>|テンプレートのコンパイルに使用される名前空間です。|
|**-I** \<includedirectory>|指定されたテキスト テンプレートに含まれるテキスト テンプレートを格納するディレクトリ。|
|**-P** \<referencepath>|またはを使用してテキスト テンプレート内で指定されたアセンブリを検索するディレクトリを**-r**オプション。<br /><br /> たとえば、Visual Studio API を使用するアセンブリは、次のように使用します。<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|名前、完全な型名と、テキスト テンプレート内のカスタム ディレクティブの処理に使用できるディレクティブ プロセッサのアセンブリ。|
|**-** [processorName] です [。directiveName] です。\<parameterName >!\<parameterValue >|ディレクティブ プロセッサのパラメーターの値を指定します。 パラメーター名と値のみを指定する場合、パラメーターはすべてのディレクティブ プロセッサを使用可能になります。 ディレクティブ プロセッサを指定する場合はこのパラメーターは指定したプロセッサでのみ使用できます。 ディレクティブ名を指定する場合、パラメーターの値は指定されたディレクティブが処理されている場合にのみ使用できます。<br /><br /> ディレクティブ プロセッサまたはテキスト テンプレートからパラメーター値にアクセスする[ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx)です。 テキスト テンプレートで、含める`hostspecific`、template ディレクティブのに対して、メッセージを呼び出すと`this.Host`です。 例えば:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`。<br /><br /> 常に入力、'!' の省略可能なプロセッサとディレクティブの名前を省略した場合でもをマークします。 例えば:<br /><br /> `-a !!param!value`|
|**-h**|ヘルプを提供します。|

## <a name="related-topics"></a>関連トピック

|タスク|トピック|
|----------|-----------|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内にファイルを生成する。|[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|独自のデータ ソースを変換するためのディレクティブ プロセッサを作成する。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|
|使用すると、独自のアプリケーションからのテキスト テンプレートを呼び出すテキスト テンプレート ホストを記述します。|[カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)|