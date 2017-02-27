---
title: "CA5350: 脆弱な暗号アルゴリズムを使用しないでください。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350: 脆弱な暗号アルゴリズムを使用しないでください。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|カテゴリ|Microsoft.Cryptography|  
|互換性に影響する変更点|中断なし|  
  
> [!NOTE]
>  この警告の最終更新は 2015 年 11 月です。  
  
## 原因  
 <xref:System.Security.Cryptography.TripleDES> などの暗号化アルゴリズムと <xref:System.Security.Cryptography.SHA1> や <xref:System.Security.Cryptography.RIPEMD160> などのハッシュ アルゴリズムは脆弱であると見なされています。  
  
 これらの暗号化アルゴリズムは、最新の暗号化アルゴリズムほどにはセキュリティが保証されません。 暗号ハッシュ アルゴリズム <xref:System.Security.Cryptography.SHA1> と <xref:System.Security.Cryptography.RIPEMD160> は、最新のハッシュ アルゴリズムよりも耐衝突性が低くなります。 暗号化アルゴリズム <xref:System.Security.Cryptography.TripleDES> は、最新の暗号化アルゴリズムよりもセキュリティ ビットの数が少なくなっています。  
  
## 規則の説明  
 現在、さまざまな理由で弱い暗号化アルゴリズムとハッシュ関数が使用されていますが、保護対象のデータの機密性を保証するためにこれらを使用しないでください。  
  
 この規則がトリガーされるのは、コードで 3DES、SHA1、RIPEMD160 のいずれかのアルゴリズムが検出され、ユーザーに警告がスローされるときです。  
  
## 違反の修正方法  
 暗号強度の高いオプションを使用します。  
  
-   TripleDES 暗号化の場合、<xref:System.Security.Cryptography.Aes> 暗号化を使用します。  
  
-   SHA1 または RIPEMD160 のハッシュ関数の場合、[SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) ファミリのいずれか \(<xref:System.Security.Cryptography.SHA512>、<xref:System.Security.Cryptography.SHA384>、<xref:System.Security.Cryptography.SHA256> など\) を使用します。  
  
## 警告を抑制する状況  
 データに必要な保護レベルがセキュリティ保証を必要としない場合には、この規則による警告を抑制してください。  
  
## 擬似コードの例  
 この記事の執筆時点では、次の擬似コード サンプルはこの規則によって検出されたパターンを示しています。  
  
### SHA\-1 ハッシュ違反  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### ソリューション  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### RIPEMD160 ハッシュ違反  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### ソリューション  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### TripleDES 暗号化違反  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### ソリューション  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```