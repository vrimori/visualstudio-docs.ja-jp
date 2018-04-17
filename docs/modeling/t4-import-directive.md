---
title: T4 インポート ディレクティブ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 05891c415e801a7d08a3b168dec854d8566363d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="t4-import-directive"></a>T4 インポート ディレクティブ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の T4 テキスト テンプレートのコード ブロックでは、`import` ディレクティブを使用することにより、完全修飾名を指定しなくても別の名前空間の要素を参照できます。 このディレクティブは、C# の `using` または `imports` の [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] に相当します。  
  
 T4 テキスト テンプレートの記述の一般的な概要については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)です。  
  
## <a name="using-the-import-directive"></a>import ディレクティブの使用  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 この例では、テンプレート コードで System.IO のメンバーの明示的な名前空間を省略できます。  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>標準インポート  
 次の名前空間は自動的にインポートされるので、この名前空間のインポート ディレクティブを記述する必要はありません。  
  
-   `System`  
  
 また、カスタム ディレクティブを使用する場合は、ディレクティブ プロセッサによって一部の名前空間が自動的にインポートされます。  
  
 たとえば、ドメイン固有言語 (DSL) のテンプレートを作成する場合、次の名前空間のインポート ディレクティブを記述する必要はありません。  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   DSL の名前空間  
  
## <a name="see-also"></a>関連項目  
 [T4 アセンブリ ディレクティブ](../modeling/t4-assembly-directive.md)