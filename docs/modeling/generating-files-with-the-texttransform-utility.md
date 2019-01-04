---
title: TextTransform ユーティリティを使用したファイルの生成
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
ms.openlocfilehash: 70a2b45bdaa637a538a71ff67619e2ddacb6c9be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870824"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform ユーティリティを使用したファイルの生成

TextTransform.exe は、テキスト テンプレートを変換するために使用できるコマンド ライン ツールです。 TextTransform.exe を呼び出すときに、引数として、テキスト テンプレート ファイルの名前を指定します。 TextTransform.exe では、テキスト変換エンジンを呼び出し、テキスト テンプレートを処理します。 TextTransform.exe は通常、スクリプトから呼び出されます。ただし、Visual Studio あるいは、ビルド プロセスの中で、テキスト変換が実行されるため、通常、必須ではありません。

> [!NOTE]
> ビルド プロセスの一部としてテキスト変換を実行する場合は、MSBuild のテキスト変換タスクの使用を検討してください。 詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)  Visual Studio がインストールされているコンピューターでは、テキスト テンプレートを変換するアプリケーションあるいは Visual Studio 拡張機能を作成することもできます。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)します。

 TextTransform.exe は、次のディレクトリにあります。

 Professional edition:

**\Program files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

 Enterprise edition:

 **\Program files (x86) \Microsoft Visual studio \2017\enterprise\common7\ide**

Visual Studio の以前のバージョンでは、次の場所にファイルがあります。

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

{version} は、インストールされている Visual Studio のバージョンによります。

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
|**-P** \<referencepath>|テキスト テンプレート内、あるいは、 **-r** オプションで指定されたアセンブリを検索するディレクトリ。<br /><br /> たとえば、Visual Studio API を使用するアセンブリを含めるためには次のようにします。<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|テキスト テンプレートの中でカスタム ディレクティブの処理に使用できるディレクティブ プロセッサの名前、完全な型の名前、および、アセンブリ。|
|**-h**|ヘルプを提供します。|

## <a name="related-topics"></a>関連トピック

|タスク|トピック|
|-|-|
|Visual Studio ソリューション中での ファイル の生成。|[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|独自のデータ ソースを変換するためのディレクティブ プロセッサの作成。|[T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)|
|独自のアプリケーションからテキスト テンプレートを呼び出すことができるテキスト テンプレート ホストの作成。|[カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)|
