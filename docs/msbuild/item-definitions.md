---
title: "項目定義 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 項目定義"
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 項目定義
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 では、[ItemGroup](../msbuild/itemgroup-element-msbuild.md) 要素を使用することにより、プロジェクト ファイルに項目を静的に宣言できます。  ただし、メタデータは、すべての項目に共通であっても項目単位でしか追加できません。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 以降には、この制限を克服する [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) という名前のプロジェクト要素が導入されました。  *ItemDefinitionGroup* を使用して一連の項目定義を定義すると、名前付きの項目の種類に含まれるすべての項目に既定のメタデータ値を追加できます。  
  
 *ItemDefinitionGroup* 要素は、プロジェクト ファイルの [Project](../msbuild/project-element-msbuild.md) 要素の直後にあります。  項目定義によって、次の機能が使用可能になります。  
  
-   項目の既定のグローバル メタデータをターゲットの外部で定義できます。  これにより、指定した種類のすべての項目に同じメタデータが適用されます。  
  
-   項目の種類には複数の定義を指定できます。  項目の種類に複数のメタデータ指定を追加すると、最後の指定が優先されます \(メタデータのインポート順序はプロパティの場合と同じです\)。  
  
-   メタデータは追加的に指定できます。  たとえば、CDefines の値は設定されるプロパティに応じて条件付きで累積されます。  たとえば、`MT;STD_CALL;DEBUG;UNICODE` のようにします。  
  
-   メタデータを削除することができます。  
  
-   条件を使用してメタデータの追加を制御できます。  
  
## 項目メタデータの既定値  
 ItemDefinitionGroup に定義された項目メタデータは、既定のメタデータの宣言に過ぎません。  ItemGroup からメタデータ値を取り込む項目を定義しない限り、ItemDefinitionGroup に定義されたメタデータは適用されません。  
  
> [!NOTE]
>  このトピックでは、多くの例に ItemDefinitionGroup 要素が示されていますが、それに対応する ItemGroup 定義は例の簡潔さを保つために省略しています。  
  
 ItemGroup に明示的に定義されたメタデータは、ItemDefinitionGroup 内のメタデータより優先されます。  ItemDefinitionGroup 内のメタデータは、ItemGroup に対応するメタデータが定義されていない場合のみ適用されます。  次のように記述します。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 この例では、項目 "i" ではメタデータ "m" が明示的に定義されていないため、既定のメタデータ "m" が項目 "i" に適用されます。  ただし、項目 "i" でメタデータ "n" が既に定義されているため、既定のメタデータ "n" は項目 "i" には適用されません。  
  
> [!NOTE]
>  XML 要素名およびパラメーター名では、大文字と小文字が区別されます。  項目メタデータ名と項目\/プロパティ名では、大文字と小文字は区別されません。  したがって、大文字と小文字のみが異なる名前の ItemDefinitionGroup 項目は同じ ItemGroup として扱う必要があります。  
  
## 値のソース  
 ItemDefinitionGroup に定義されたメタデータには、以下のさまざまなソースから値を割り当てることができます。  
  
-   PropertyGroup プロパティ  
  
-   ItemDefinitionGroup 内の項目  
  
-   ItemDefinitionGroup 項目の項目変換  
  
-   環境変数  
  
-   グローバル プロパティ \(MSBuild.exe コマンド ラインで指定\)  
  
-   予約済みのプロパティ  
  
-   ItemDefinitionGroup 内の項目の既知のメタデータ  
  
-   CDATA セクション \<\!\[CDATA\[この部分は解析されない\]\]\>  
  
> [!NOTE]
>  ItemDefinitionGroup 要素は ItemGroup 要素より先に処理されるため、ItemGroup の項目メタデータは ItemDefinitionGroup メタデータの宣言では役に立ちません。  
  
## 追加が可能な複数の定義  
 定義を追加したり複数の ItemDefinitionGroup を使用したりするときには、次の点に注意してください。  
  
-   追加のメタデータ指定は、その型に追加されます。  
  
-   最後のメタデータ指定が優先されます。  
  
 複数の ItemDefinitionGroup がある場合、それ以降メタデータ指定を行うたびに、そのメタデータが前の定義に追加されます。  次のように記述します。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 この例では、メタデータ "o" が "m" および "n" に追加されます。  
  
 さらに、定義済みのメタデータ値も追加できます。  次のように記述します。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 この例では、メタデータ "m" \(m1\) の定義済みの値が新しい値 \(m2\) に追加されるため、最終的な値は "m1;m2" となります。  
  
> [!NOTE]
>  これは同じ ItemDefinitionGroup でも発生します。  
  
 定義済みのメタデータ指定をオーバーライドすると、最後の指定が優先されます。  次の例では、メタデータ "m" の最終的な値が "m1" から "m1a" に変わります。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## ItemDefinitionGroup での条件の使用  
 ItemDefinitionGroup では、条件を使用してメタデータの追加を制御できます。  次のように記述します。  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 この例では、"Configuration" プロパティの値が "Debug" である場合のみ項目 "i" の既定のメタデータ "m1" が追加されます。  
  
> [!NOTE]
>  条件では、ローカル メタデータ参照のみサポートされます。  
  
 前の ItemDefinitionGroup に定義されたメタデータへの参照は、定義グループではなく項目に対してローカルです。  つまり、参照は項目をスコープとします。  次のように記述します。  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 この例では、項目 "i" が条件に含まれる項目 "test" を参照しています。  
  
## メタデータのオーバーライドと削除  
 ItemDefinitionGroup 要素に定義されたメタデータは、値を空白に設定することにより、後の ItemDefinitionGroup 要素でオーバーライドできます。  また、メタデータ項目は空の値に設定することによって削除できます。  次のように記述します。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 項目 "i" はメタデータ "m" を含んでいますが、その値は空です。  
  
## メタデータのスコープ  
 ItemDefinitionGroup は、それが定義されている定義済みプロパティおよびグローバル プロパティの全体をスコープとします。  ItemDefinitionGroup 内の既定のメタデータ定義は自己参照が可能です。  たとえば、次の例では簡単なメタデータ参照を使用しています。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 次のような修飾されたメタデータ参照も使用できます。  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 ただし、次のコードは無効です。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 以降では、ItemGroup も自己参照が可能です。  次のように記述します。  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## 参照  
 [バッチ](../msbuild/msbuild-batching.md)