---
title: "CA1058: 型は、一定の基本型を拡張することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1058: 型は、一定の基本型を拡張することはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能な型では、特定の基本型が拡張されます。  現在、この規則では次の型から派生した型が報告されます。  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## 規則の説明  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 1 では、<xref:System.ApplicationException> から新しい例外を派生することが推奨されていました。  この推奨事項は変更されました。新しい例外は、<xref:System.Exception?displayProperty=fullName> または <xref:System> 名前空間のサブクラスの 1 つから派生する必要があります。  
  
 基となるオブジェクト モデルまたはデータ ソースの XML ビューを作成する場合、<xref:System.Xml.XmlDocument> のサブクラスを作成しないでください。  
  
### 非ジェネリック コレクション  
 可能な限りジェネリック コレクションを使用または拡張するようにします。  以前に提供済みである場合を除き、コード内で非ジェネリック コレクションを拡張しないでください。  
  
 **間違った使用例**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **正しい使用例**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## 違反の修正方法  
 この規則違反を修正するには、別の基本型またはジェネリック コレクションから型を派生します。  
  
## 警告を抑制する状況  
 <xref:System.ApplicationException> に関する違反については、この規則による警告を抑制しないでください。  <xref:System.Xml.XmlDocument> に関する違反については、この規則による警告を抑制しても安全です。  以前にコードをリリース済みである場合は、非ジェネリック コレクションに関する警告を抑制しても安全です。