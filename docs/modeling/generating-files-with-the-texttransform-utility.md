---
title: "TextTransform ユーティリティを使用してファイルを生成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>TextTransform ユーティリティを使用したファイルの生成
TextTransform.exe は、テキスト テンプレートを変換するのに使用できるコマンド ライン ツールです。 TextTransform.exe を呼び出すときに、引数として、テキスト テンプレート ファイルの名前を指定します。 TextTransform.exe は、テキスト変換エンジンを呼び出し、テキスト テンプレートを処理します。 TextTransform.exe は通常、スクリプトから呼び出されます。 ただし、それは通常必要ありません、テキスト変換を実行するには、Visual Studio で、またはビルド処理のためです。  
  
> [!NOTE]
>  ビルド プロセスの一部としてのテキスト変換を実行する場合は、MSBuild のテキスト変換タスクの使用を検討します。 詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)します。 いるコンピューターでの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]がインストールされているアプリケーションを記述することもできます。 または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートを変換できる拡張機能です。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)します。  
  
 TextTransform.exe は、次のディレクトリにあります。  
  
 **\Program files \microsoft Shared\TextTemplating\11.0**  
  
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
|**-アウト** \<filename >|変換の出力が書き込まれるファイルです。|  
|**-r** \<アセンブリ >|アセンブリをコンパイルして、テキスト テンプレートを実行するに使用します。|  
|**-u** \<名前空間 >|テンプレートのコンパイルに使用される名前空間。|  
|**-I** \<includedirectory >|指定されたテキスト テンプレートに含まれるテキスト テンプレートを格納するディレクトリ。|  
|**-P** \<referencepath >|またはを使用して、テキスト テンプレート内で指定されたアセンブリを検索するディレクトリを**-r**オプション。<br /><br /> たとえば、Visual Studio API を使用するアセンブリは、次のように使用します。<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\<className > です。\<assemblyName | コードベース >|名前、完全な型名、およびテキスト テンプレート内のカスタム ディレクティブの処理に使用できるディレクティブ プロセッサのアセンブリ。|  
|**-a** [processorName]! [directiveName] です。\<parameterName >!\<parameterValue >|ディレクティブ プロセッサのパラメーターの値を指定します。 パラメーター名と値のみを指定するパラメーターはすべてのディレクティブ プロセッサになります。 ディレクティブ プロセッサを指定する場合は、パラメーターを指定されたプロセッサでのみ使用できます。 ディレクティブの名前を指定する場合、パラメーターの値は指定ディレクティブが処理されている場合にのみ使用します。<br /><br /> ディレクティブ プロセッサまたはテキスト テンプレートからパラメーター値にアクセスするには、 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>。</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>を使用します。 テキスト テンプレートに含める`hostspecific`template ディレクティブにに対してメッセージを呼び出すと`this.Host`です。 例:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`。<br /><br /> 常に入力、'!' の省略可能なプロセッサとディレクティブの名前を省略した場合でもをマークします。 例:<br /><br /> `-a !!param!value`|  
|**-h**|ヘルプを提供します。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タスク|トピック|  
|----------|-----------|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内にファイルを生成する。|[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|独自のデータ ソースを変換するためのディレクティブ プロセッサを作成する。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|  
|使用すると、独自のアプリケーションからのテキスト テンプレートを呼び出すテキスト テンプレート ホストを記述します。|[カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)|
