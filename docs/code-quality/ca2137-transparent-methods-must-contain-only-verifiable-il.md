---
title: "Ca 2137: 透過的メソッドは検証可能な IL のみを含める必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70a7574e0379c8e4b8dc9a888185efceb480fad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: 透過的メソッドは、検証可能な IL のみを含まなければならない
|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッドに検証できないコードが含まれているか、メソッドから参照渡しで型が返されます。  
  
## <a name="rule-description"></a>規則の説明  
 この規則は、透過的セキュリティ コードが、検証できない MSIL (Microsoft Intermediate Language) を実行しようとすると適用されます。 ただし、規則には完全な IL 検証ツールは含まれていないため、代わりにヒューリスティックを使用して、ほとんどの MSIL 検証違反が検出されます。  
  
 実行するのには特定のコードにだけ検証可能な MSIL が含まれている、 [Peverify.exe (PEVerify ツール)](/dotnet/framework/tools/peverify-exe-peverify-tool)アセンブリにします。 PEVerify でを実行、 **/transparent**オプションにのみ検証不可能なする透過的メソッドが原因でエラー出力を制限します。 場合、/、透過的なオプションを使用しない、PEVerify も検証不可能なコードを含めることができる重要なメソッドを確認します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するを使用してメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性、または検証不可能なコードを削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 この例ではメソッドが検証できないコードを使用してでマークする必要があります、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。  
  
 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]