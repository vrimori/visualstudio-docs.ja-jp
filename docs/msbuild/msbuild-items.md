---
title: "MSBuild 項目 | Microsoft Docs"
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
  - "MSBuild 項目"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 項目はビルド システムへの入力され、通常のファイルを表します。 項目は、要素名に基づいて項目の種類にグループ化されます。 項目の種類は項目の名前付きリストであり、タスクのパラメーターとして使用できます。 タスクは項目値を使用して、ビルド処理のステップを実行します。  
  
 所属する項目の種類によっては、項目が名前付き、ため、用語"item"と「アイテムの値」ように使用できます。  
  
 **このトピックの内容**  
  
-   [プロジェクト ファイル内の項目を作成します。](#BKMK_Creating1)  
  
-   [実行時に項目を作成します。](#BKMK_Creating2)  
  
-   [プロジェクト ファイル内の項目を参照します。](#BKMK_ReferencingItems)  
  
-   [項目を指定するワイルドカードを使用します。](#BKMK_Wildcards)  
  
-   [Exclude 属性を使用します。](#BKMK_ExcludeAttribute)  
  
-   [項目メタデータ](#BKMK_ItemMetadata)  
  
    -   [プロジェクト ファイル内のアイテムのメタデータの参照](#BKMK_ReferencingItemMetadata)  
  
    -   [既知のアイテム メタデータ](#BKMK_WellKnownItemMetadata)  
  
    -   [メタデータを使用して項目の種類を変換します。](#BKMK_Transforming)  
  
-   [項目の定義](#BKMK_ItemDefinitions)  
  
-   [ターゲットの ItemGroup の項目の属性](#BKMK_AttributesWithinTargets)  
  
    -   [属性を削除します。](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata 属性](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata 属性](#BKMK_RemoveMetadata)  
  
    -   [KeepDuplicates 属性](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> プロジェクト ファイル内の項目を作成します。  
 プロジェクト ファイル内の項目の子としての要素を宣言、 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 要素。 子要素の名前は、項目の種類です。  `Include` 要素の属性は、その項目の種類に含まれる項目 (ファイル) を指定します。 たとえば、次の XML がという項目の種類を作成 `Compile`, 、2 つのファイルを含めています。  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 "File2.cs"項目が項目"file1.cs"; に置き換わりません値のリストにファイル名を追加する代わりに、 `Compile` 項目の種類。 ビルドの評価フェーズ中に、項目の種類から項目を削除することはできません。  
  
 次の XML は、両方のファイルでいずれかを宣言することで同じ項目の種類を作成 `Include` 属性です。 ファイル名が、セミコロンで区切られたことに注意してください。  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> 実行時に項目を作成します。  
 外部にある項目 [ターゲット](../msbuild/target-element-msbuild.md) 要素には、ビルドの評価フェーズ中に値が割り当てられます。 その後の実行フェーズの項目を作成または次のように変更します。  
  
-   任意のタスクは、項目を生成できます。 項目を出力する、 [タスク](../msbuild/task-element-msbuild.md) 要素が子を持つことは [出力](../msbuild/output-element-msbuild.md) を持つ要素、 `ItemName` 属性です。  
  
-    [CreateItem](../msbuild/createitem-task.md) タスクは、項目を生成できます。 この使用法は推奨されていません。  
  
-   .NET Framework 3.5 以降では `Target` 要素を含めることが [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目要素の要素を含むことがあります。  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> プロジェクト ファイル内の項目を参照します。  
 プロジェクト ファイルで項目の種類を参照する構文を使用する @(`ItemType`)。 たとえばを使用して前の例では、項目の種類を参照 `@(Compile)`します。 この構文を使用すると、そのタスクのパラメーターとして、項目の種類を指定することによって、タスクに項目を渡すことができます。 詳細については、次を参照してください。 [方法: ビルドするファイルの選択](../msbuild/how-to-select-the-files-to-build.md)します。  
  
 既定では、展開されているときに、セミコロン (;) で、項目の種類のアイテムが区別されます。 構文を使用する @(*ItemType*, 、'*区切り記号*') に既定以外の区切り記号を指定します。 詳細については、次を参照してください。 [方法: 表示、項目リストをコンマ区切りで](../msbuild/how-to-display-an-item-list-separated-with-commas.md)します。  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> 項目を指定するワイルドカードを使用します。  
 使用する、* *、 \*, 、およびでしょうか。 ワイルドカードを使用すると、各ファイルを個別に一覧表示ではなく、ビルドの入力としてファイルのグループを指定します。  
  
-   ですか。 ワイルドカード文字では、単一の文字と一致します。  
  
-   * ワイルドカード文字が 0 個以上の文字と一致します。  
  
-   * * ワイルドカード文字のシーケンスには、部分的なパスと一致します。  
  
 たとえば、プロジェクト ファイルで次の要素を使用して、プロジェクト ファイルを含むディレクトリで、すべての .cs ファイルを指定できます。  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 次の要素は、d: ドライブ上のすべての .vb ファイルを選択します。  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 ワイルドカード文字の詳細については、次を参照してください。 [方法: ビルドするファイルの選択](../msbuild/how-to-select-the-files-to-build.md)します。  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Exclude 属性を使用します。  
 項目の要素を含めることができます、 `Exclude` 属性で、項目の種類から特定の項目 (ファイル) を除外します。  `Exclude` 属性は、通常、ワイルドカード文字と共に使用します。 たとえば、次の XML に追加されて、ディレクトリ内のすべての .cs ファイル CSFile 項目の種類を除く、 `DoNotBuild.cs` ファイルです。  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
  `Exclude` 属性によって追加された項目のみに影響を与えます、 `Include` その両方を含む項目要素の属性です。 次の例では、前の項目要素で追加された Form1.cs ファイルを除外はありません。  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 詳細については、次を参照してください。 [方法: ビルドから除外するファイル](../msbuild/how-to-exclude-files-from-the-build.md)します。  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> 項目メタデータ  
 項目の情報に加えて、メタデータを含めることが、 `Include` と `Exclude` 属性です。 このメタデータは、項目に関するまたはバッチ タスクとコア ターゲットの詳細を必要とするタスクで使用できます。 詳細については、次を参照してください。 [バッチ処理](../msbuild/msbuild-batching.md)します。  
  
 メタデータは、item 要素の子要素として、プロジェクト ファイルで宣言されているキー/値ペアのコレクションです。 子要素の名前は、メタデータの名前と、子要素の値は、メタデータの値。  
  
 メタデータは、それを含む項目要素に関連付けられます。 たとえば、次の XML が追加されて `Culture` メタデータ値を持つ `Fr` "one.cs"と、CSFile の"two.cs"アイテムの両方に項目の種類。  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 項目には 0 以上のメタデータ値を指定できます。 メタデータの値は、いつでも変更できます。 メタデータを空の値に設定すると、効果的にから削除した場合、ビルドします。  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> プロジェクト ファイル内のアイテムのメタデータの参照  
 プロジェクト ファイルで項目のメタデータを参照するには、構文の使用を %(`ItemMetadataName`)。 あいまいさが存在する場合は、項目の種類の名前を使用して参照を修飾することができます。 たとえば、設定できる %(*ItemType.ItemMetaDataName*)。次の例では、メタデータの表示を使用して、メッセージ タスクのバッチします。 バッチ処理のアイテム メタデータを使用する方法の詳細については、次を参照してください。 [タスクのバッチの項目メタデータ](../msbuild/item-metadata-in-task-batching.md)します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> 既知のアイテム メタデータ  
 項目が項目の種類に追加されると、その項目には、既知のメタデータが割り当てられます。 たとえば、すべての項目が、既知のメタデータをある `%(Filename)`, 、した項目のファイル名の値を保持します。 詳細については、次を参照してください。 [既知のアイテム メタデータ](../msbuild/msbuild-well-known-item-metadata.md)します。  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> メタデータを使用して項目の種類を変換します。  
 メタデータを使用して、新しい項目リストに項目リストを変換できます。 たとえば、項目の種類を変換する `CppFiles` .obj ファイルの対応する一覧に、式を使用しての .cpp ファイルを表す項目を含む `@(CppFiles -> '%(Filename).obj')`します。  
  
 次のコード作成、 `CultureResource` 項目の種類のすべてのコピーを含む `EmbeddedResource` を持つアイテムを `Culture` メタデータ。  `Culture` メタデータ値が、新しいメタデータの値になります `CultureResource.TargetDirectory`します。  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 詳細については、次を参照してください。 [変換](../msbuild/msbuild-transforms.md)します。  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> 項目の定義  
 以降、.NET Framework 3.5 では、追加できます既定のメタデータ、項目の種類を使用して、 [ItemDefinitionGroup 要素](../msbuild/itemdefinitiongroup-element-msbuild.md)します。 よく知られているメタデータと同様に、既定のメタデータは、指定した項目の種類のすべての項目に関連付けられます。 既定のメタデータ項目の定義で明示的にオーバーライドできます。 たとえば、次の XML は、 `Compile` アイテム"one.cs"や"three.cs"メタデータ `BuildDay` "Monday"の値を使用します。 このコードは項目"two.cs"のメタデータを得られます `BuildDay` "Tuesday"の値を使用します。  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 詳細については、次を参照してください。 [項目定義](../msbuild/item-definitions.md)します。  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> ターゲットの ItemGroup の項目の属性  
 .NET Framework 3.5 以降では `Target` 要素を含めることが [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目要素の要素を含むことがあります。 項目で指定されているときに、このセクションの属性が有効な `ItemGroup` 内にある、 `Target`です。  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> 属性を削除します。  
 [項目を `ItemGroup` のターゲットを含めることが、 `Remove` 属性で、項目の種類から特定の項目 (ファイル) を削除します。 この属性は、.NET Framework 3.5 で導入されました。  
  
 次の例では、項目の種類 Compile からすべての .config ファイルを削除します。  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata 属性  
 Item 要素を含めることができます、ターゲット内の項目が生成された場合、 `KeepMetadata` 属性です。 この属性を指定すると、その名のセミコロン区切りのリストで指定されているメタデータのみはターゲット アイテムにソース アイテムから転送されます。 この属性を空の値を指定しないと同じです。  `KeepMetadata` 属性は、.NET Framework 4.5 で導入されました。  
  
 次の例では、使用する方法、 `KeepMetadata` 属性です。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata 属性  
 Item 要素を含めることができます、ターゲット内の項目が生成された場合、 `RemoveMetadata` 属性です。 この属性が指定されている場合のすべてのメタデータがソース アイテムから、ターゲット アイテムに転送メタデータ以外の名前、セミコロンで区切られたリストに名前が含まれています。 この属性を空の値を指定しないと同じです。  `RemoveMetadata` 属性は、.NET Framework 4.5 で導入されました。  
  
 次の例では、使用する方法、 `RemoveMetadata` 属性です。  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates 属性  
 Item 要素を含めることができます、ターゲット内の項目が生成された場合、 `KeepDuplicates` 属性です。 `KeepDuplicates`  `Boolean` 項目が既存のアイテムの完全な複製である場合に、項目がターゲット グループに追加するかどうかを指定する属性です。  
  
 項目が追加されたソースとターゲットのアイテムには、さまざまなメタデータが、同じインクルード値がある、たとえ `KeepDuplicates` に設定されている `false`します。 この属性を空の値を指定しないと同じです。  `KeepDuplicates` 属性は、.NET Framework 4.5 で導入されました。  
  
 次の例では、使用する方法、 `KeepDuplicates` 属性です。  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>関連項目  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [方法: ビルドするファイルの選択](../msbuild/how-to-select-the-files-to-build.md)   
 [方法: ビルドからファイルを除外します。](../msbuild/how-to-exclude-files-from-the-build.md)   
 [方法: 項目リストをコンマ区切りで表示](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [項目の定義](../msbuild/item-definitions.md)   
 [バッチ処理](../msbuild/msbuild-batching.md)   
 [Item 要素 (MSBuild)](../msbuild/item-element-msbuild.md)