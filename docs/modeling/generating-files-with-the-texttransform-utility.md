---
title: Visual Studio における TextTransform ユーティリティを使用したファイルの生成
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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6572ef97027466fa97c254664327f2f77b4ea7f2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967082"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform ユーティリティを使用したファイルの生成

TextTransform.exe は、テキスト テンプレートを変換するために使用できるコマンド ライン ツールです。 TextTransform.exe を呼び出すときに、引数として、テキスト テンプレート ファイルの名前を指定します。 TextTransform.exe では、テキスト変換エンジンを呼び出し、テキスト テンプレートを処理します。 TextTransform.exe は通常、スクリプトから呼び出されます。 ただし、Visual Studio あるいは、ビルド プロセスの中で、テキスト変換が実行されるため、通常、必須ではありません。

> [!NOTE]
> ビルド プロセスの一部としてテキスト変換を実行する場合は、MSBuild のテキスト変換タスクを使用して検討してください。 詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)します。 Visual Studio がインストールされているコンピューターでにアプリケーションまたはテキスト テンプレートを変換できる、Visual Studio 拡張機能を記述することもできます。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)します。

 TextTransform.exe は、次のディレクトリにあります。

 **\Program files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional edition、または

 **\Program files (x86) \Microsoft Visual studio \2017\enterprise\common7\ide**

 Enterprise edition。

Visual Studio の以前のバージョンでは、次の場所にファイルがあります。

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

場所 {0} のバージョン} は、インストールされている以前のバージョンに依存します。

## <a name="syntax"></a>構文

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>パラメーター

|**引数**|**説明**|
|-|-|
|`templateName`|変換するテンプレート ファイルの名前を示します。|

|**オプション**|**説明**|
|-|-|
|**-out** \<filename>|変換の出力を書き込むファイル。|
|**-r** \<assembly>|テキスト テンプレートをコンパイルし実行するために使用するアセンブリ。|
|**-u** \<namespace>|テンプレートのコンパイルに使用される名前空間。|
|**-I** \<includedirectory>|テキスト テンプレートでインクルードすることが指定されたテキスト テンプレートが含まれるディレクトリ。|
|**-P** \<referencepath>|またはを使用して、テキスト テンプレート内で指定されたアセンブリを検索するディレクトリを **-r**オプション。<br /><br /> たとえば、Visual Studio API を使用するアセンブリは、次のように使用します。<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|テキスト テンプレートの中でカスタム ディレクティブの処理に使用できるディレクティブ プロセッサの名前、完全な型の名前、および、アセンブリ。|
|**-** [processorName] [。directiveName]。\<parameterName >!\<parameterValue >|ディレクティブ プロセッサのパラメーター値を指定します。 パラメーター名と値のみを指定するパラメーターはすべてのディレクティブ プロセッサにできます。 ディレクティブ プロセッサを指定する場合、パラメーターが指定したプロセッサでのみ使用できます。 ディレクティブの名前を指定する場合、パラメーターの値は、指定されたディレクティブが処理されている場合にのみ使用です。<br /><br /> ディレクティブ プロセッサまたはテキスト テンプレートからパラメーター値にアクセスするには、使用[ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))します。 テキスト テンプレートでは、 `hostspecific` template ディレクティブでのメッセージを呼び出すと`this.Host`。 例えば:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`。<br /><br /> 入力を常に、'!' の省略可能なプロセッサとディレクティブの名前を省略した場合でも、マークします。 例えば:<br /><br /> `-a !!param!value`|
|**-h**|ヘルプを提供します。|

## <a name="related-topics"></a>関連トピック

|タスク|トピック|
|-|-|
|Visual Studio ソリューション中での ファイル の生成。|[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|独自のデータ ソースを変換するためのディレクティブ プロセッサの作成。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|
|独自のアプリケーションからテキスト テンプレートを呼び出すことができるテキスト テンプレート ホストの作成。|[カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)|
