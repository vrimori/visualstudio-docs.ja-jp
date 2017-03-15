---
title: "&#39;&lt;typename&gt;&#39; は &#39;My&#39; グループ内で公開されている別の型と同じ名前です。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; は &#39;My&#39; グループ内で公開されている別の型と同じ名前です。
'\<typename\>' は 'My' グループ内で公開されている別の型と同じ名前です。 フォームまたはそれを囲む名前空間の名前を変更してください。  
  
 いずれか 1 つの `My` オブジェクトのクラスまたは構造体と同じ名前でクラスまたは構造体が宣言されています。  
  
 `My.Forms` などの `My` オブジェクト経由でアクセスできる 2 つのクラス間で、名前の競合を回避することはできません。  
  
 `My` オブジェクトのクラス間で名前が競合している可能性がある場合、コンパイラは型のプロパティ名を *ClassName* から *RootNamespace*\_*Namespace*\_*ClassName* に変更します。 たとえば、`Form1` という名前の 2 つのフォームがあるとします。 これらのフォームのいずれかがルート名前空間 `WindowsApplication1` および名前空間 `Namespace1` にある場合は、`My.Forms.WindowsApplication1_Namespace1_Form1` を通じてそのフォームにアクセスします。  
  
 このエラーは、名前にアンダースコアが含まれた名前空間が入れ子になり、その中に名前が同じ 2 つのクラスがある場合に発生する可能性があります。 コンパイラがクラスの新しいプロパティ名を作成する場合に、引き続き名前の競合があります。  
  
 **エラー ID:** BC36015  
  
### このエラーを解決するには  
  
1.  新しいフォームの名前を変更します。  
  
2.  名前空間の名前を変更します。  
  
     既存のクラスまたは構造体と同じ名前をクラスまたは構造体に付けないでください。  
  
## 参照  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [ビルド内にありません: 同じ名前を持つ複数の変数がある場合に参照を解決する](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [My.Forms Object](/dotnet/visual-basic/language-reference/objects/my-forms-object)