---
title: T4 インポート ディレクティブ
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b0e641ca9eafb0fb78dbe42e2deb936db8fd840b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916024"
---
# <a name="t4-import-directive"></a>T4 インポート ディレクティブ

`import`ディレクティブにより、Visual Studio T4 テキスト テンプレートのコード ブロックにおいて、完全修飾名を指定せずに別の名前空間内の要素を参照を使用することができるようになります。 このディレクティブは、C# の `using` または、[!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]の `imports` に相当します。

T4 テキスト テンプレートの作成方法の一般的な概要については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-import-directive"></a>import ディレクティブの使用

```
<#@ import namespace="namespace" #>
```

 次の例では、テンプレート コードで System.IO のメンバーの名前空間の明示を省略できます。

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>標準インポート
 次の名前空間は自動的にインポートされるので、この名前空間のインポート ディレクティブを記述する必要はありません。

- `System`

  また、カスタム ディレクティブを使用する場合は、ディレクティブ プロセッサによって一部の名前空間が自動的にインポートされます。

  たとえば、ドメイン固有言語 (DSL) のテンプレートを作成する場合、次の名前空間のインポート ディレクティブを記述する必要はありません。

- `Microsoft.VisualStudio.Modeling`

- DSL の名前空間

## <a name="see-also"></a>関連項目

- [T4 アセンブリ ディレクティブ](../modeling/t4-assembly-directive.md)