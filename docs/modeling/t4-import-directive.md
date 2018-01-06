---
title: "T4 インポート ディレクティブ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 5d581e182b39ac5a786b2d66a1a3798ba7fe82ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [T4 アセンブリ ディレクティブ](../modeling/t4-assembly-directive.md)