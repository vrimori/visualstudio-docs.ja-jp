---
title: "CA2229: シリアル化コンストラクターを実装します | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229: シリアル化コンストラクターを実装します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> インターフェイスを実装している型が、デリゲートでもインターフェイスでもなく、次の条件のいずれかに当てはまります。  
  
-   この型に、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> オブジェクトと <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> オブジェクト \(シリアル化コンストラクターのシグネチャ\) を使用するコンストラクターがありません。  
  
-   この型はシールされていません。またシリアル化コンストラクターのアクセス修飾子が保護されていません \(ファミリではありません\)。  
  
-   この型はシールされています。またシリアル化コンストラクターのアクセス修飾子がプライベートではありません。  
  
## 規則の説明  
 この規則は、カスタムのシリアル化をサポートする型に関係があります。  型で <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する場合、カスタムのシリアル化がサポートされます。  シリアル化コンストラクターは、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> メソッドを使用してシリアル化されたオブジェクトの逆シリアル化、または再作成に必要です。  
  
## 違反の修正方法  
 この規則違反を修正するには、シリアル化コンストラクターを実装します。  シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。  
  
## 警告を抑制する状況  
 この規則の警告は抑制しないでください。  このような型は逆シリアル化できません。また多くの状況で正常に機能しません。  
  
## 使用例  
 この規則に適合する型を次の例に示します。  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## 関連規則  
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## 参照  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>