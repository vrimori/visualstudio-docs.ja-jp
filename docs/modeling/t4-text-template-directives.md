---
title: T4 テキスト テンプレートのディレクティブ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 3bf8248a7a68b914d6276e3e6f37261fb6137efc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939253"
---
# <a name="t4-text-template-directives"></a>T4 テキスト テンプレートのディレクティブ
ディレクティブは、テキスト テンプレート変換エンジンに対する命令です。

 ディレクティブの構文は次のとおりです。

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

 属性値はすべて、二重引用符で囲む必要があります。 値そのものに引用符が含まれている場合は、\ 文字でエスケープする必要があります。

 通常、ディレクティブはテンプレート ファイルまたはインクルード ファイル内の最初の要素となります。 コード ブロック (`<#...#>`) 内およびクラス機能ブロック (`<#+...#>`) の後に、ディレクティブを配置することはできません。

 [T4 テンプレート ディレクティブ](../modeling/t4-template-directive.md)
 ```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)
 ```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 [T4 出力ディレクティブ](../modeling/t4-output-directive.md)
 ```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 [T4 アセンブリ ディレクティブ](../modeling/t4-assembly-directive.md)
 ```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)
 ```
<#@ import namespace="namespace" #>
```

 [T4 インクルード ディレクティブ](../modeling/t4-include-directive.md)
 ```
<#@ include file="filePath" #>
```

 [T4 CleanUpBehavior ディレクティブ](../modeling/t4-cleanupbehavior-directive.md)
 ```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

 独自のディレクティブを作成することもできます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md) Visualization and Modeling SDK を使用してドメイン固有言語 (DSL) を作成すると、DSL の一部としてディレクティブ プロセッサが生成されます。