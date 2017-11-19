---
title: "TextTransform ユーティリティを使用してファイルを生成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: "41"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1d168695aca3626fa1ba351aef56faf001c5b6ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generating-files-with-the-texttransform-utility"></a>TextTransform ユーティリティを使用したファイルの生成
TextTransform.exe は、テキスト テンプレートを変換するのに使用できるコマンド ライン ツールです。 TextTransform.exe を呼び出すときに、引数として、テキスト テンプレート ファイルの名前を指定します。 TextTransform.exe は、テキスト変換エンジンを呼び出し、テキスト テンプレートを処理します。 TextTransform.exe は通常、スクリプトから呼び出されます。 ただし、これは通常必要ありません、テキスト変換を実行するには、Visual Studio で、または、ビルド処理のためです。  
  
> [!NOTE]
>  ビルド プロセスの一環として、テキスト変換を実行する場合は、MSBuild テキスト変換タスクを使用することを検討します。 詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)です。 ためのコンピューターで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]がインストールされているアプリケーションを記述することもできます。 または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートを変換できる拡張機能です。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)です。  
  
 TextTransform.exe は、次のディレクトリにあります。  
  
 **\Program files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**  

Professional edition、または

 **\Program files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**
 
 Enterprise エディションです。

Visual Studio の以前のバージョンで、次の場所にファイルが見つかりました。

**\Program files (x86) \common Shared\TextTemplating\{バージョン}**

ここで {のバージョン} は、インストールされている以前のバージョンに依存します。

## <a name="syntax"></a>構文  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|**引数**|**説明**|  
|------------------|---------------------|  
|`templateName`|変換するテンプレート ファイルの名前を識別します。|  
  
|**オプション**|**説明**|  
|----------------|---------------------|  
|**-アウト**\<ファイル名 >|変換の出力の書き込み先となるファイル。|  
|**-r** \<アセンブリ >|アセンブリをコンパイルすると、テキスト テンプレートを実行するために使用します。|  
|**-u** \<名前空間 >|テンプレートのコンパイルに使用される名前空間です。|  
|**-I** \<includedirectory >|指定されたテキスト テンプレートに含まれるテキスト テンプレートを格納するディレクトリ。|  
|**-P** \<referencepath >|またはを使用してテキスト テンプレート内で指定されたアセンブリを検索するディレクトリを**-r**オプション。<br /><br /> たとえば、Visual Studio API を使用するアセンブリは、次のように使用します。<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\<クラス名 >!\<assemblyName &#124; codeBase >|名前、完全な型名と、テキスト テンプレート内のカスタム ディレクティブの処理に使用できるディレクティブ プロセッサのアセンブリ。|  
|**-** [processorName] です [。directiveName] です。\<parameterName >!\<parameterValue >|ディレクティブ プロセッサのパラメーターの値を指定します。 パラメーター名と値のみを指定する場合、パラメーターはすべてのディレクティブ プロセッサを使用可能になります。 ディレクティブ プロセッサを指定する場合はこのパラメーターは指定したプロセッサでのみ使用できます。 ディレクティブ名を指定する場合、パラメーターの値は指定されたディレクティブが処理されている場合にのみ使用できます。<br /><br /> ディレクティブ プロセッサまたはテキスト テンプレートからパラメーター値にアクセスする<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>です。 テキスト テンプレートで、含める`hostspecific`、template ディレクティブのに対して、メッセージを呼び出すと`this.Host`です。 例:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`。<br /><br /> 常に入力、'!' の省略可能なプロセッサとディレクティブの名前を省略した場合でもをマークします。 例:<br /><br /> `-a !!param!value`|  
|**-h**|ヘルプを提供します。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タスク|トピック|  
|----------|-----------|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内にファイルを生成する。|[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|独自のデータ ソースを変換するためのディレクティブ プロセッサを作成する。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|  
|使用すると、独自のアプリケーションからのテキスト テンプレートを呼び出すテキスト テンプレート ホストを記述します。|[カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)|
