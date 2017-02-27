---
title: "項目用の関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 項目用の関数"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 項目用の関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 4.0 以降では、タスクおよびターゲットのコードで項目関数を呼び出して、プロジェクト内の項目に関する情報を取得できます。  これらの関数により、Distinct\(\) 項目の取得が簡素化され、項目をループ処理するよりも処理が速くなります。  
  
## Stringの項目関数  
 .NET Frameworkの項目の値を操作するには、文字列のメソッドとプロパティを使用できます。  <xref:System.String> のメソッドの場合、メソッドの名前を指定します。  <xref:System.String> のプロパティに、「get\_」の後にプロパティ名を指定します。  
  
 各文字列に対して文字列、文字列のメソッドまたはプロパティの実装がある項目の場合は。  
  
 次の例は、これらの文字列の項目関数を使用する方法を示します。  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## 組み込み項目関数  
 次の表に、項目に対して使用できる組み込み関数を示します。  
  
|Function|例|説明|  
|--------------|-------|--------|  
|`Count`|`@(MyItem->Count())`|項目数を返します。|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|各項目の `Path.DirectoryName` の値を返します。|  
|`Distinct`|`@(MyItem->Distinct())`|`Include` の値を持つ項目を返します。  メタデータは無視されます。  比較では、大文字と小文字を区別しません。|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|`itemspec` の値を持つ項目を返します。  メタデータは無視されます。  比較では、大文字と小文字を区別します。|  
|`Reverse`|`@(MyItem->Reverse())`|逆の項目を返します。|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|`boolean` をどの項目が、指定されたメタデータの名前と値が存在するかどうかを示すを返します。  比較では、大文字と小文字を区別しません。|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|オフのメタデータ項目を返します。  `itemspec` のみが保持されます。|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|特定のメタデータの名前の項目を返します。  比較では、大文字と小文字を区別しません。|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|メタデータの名前を持つメタデータ値を返します。|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|指定されたメタデータの名前と値を持つ項目を返します。  比較では、大文字と小文字を区別しません。|  
  
 次の例は、基本的な項目関数を使用する方法を示します。  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## 参照  
 [項目](../msbuild/msbuild-items.md)