---
title: "MSBuild 変換 | Microsoft Docs"
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
  - "MSBuild, 変換"
  - "変換 [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 変換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

変換とは、1 つの項目コレクションを別の項目リストに一対一で変換することです。  プロジェクトで項目リストを変換できます。さらに変換により、ターゲットは入出力間の直接割り当てを指定できるようになります。  このトピックでは、変換と [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] で変換を使用してより効率的にプロジェクトをビルドする方法について説明します。  
  
## 変換の修飾子  
 変換は任意ではなく、特別な構文で制限されています。すべての変換の修飾子は、%\(*ItemMetaDataName*\) という形式である必要があります。  任意の項目メタデータを変換の修飾子として使用できます。  これには、作成時にすべての項目に割り当てられる既知の項目メタデータが含まれます。  既知のアイテム メタデータの一覧については、「[Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md)」を参照してください。  
  
 次の例では、.resx ファイルの一覧を .resources ファイルの一覧に変換します。  変換の修飾子 %\(filename\) は、各 .resources ファイルが対応する .resx ファイルと同じファイル名を持つことを指定します。  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  変換された項目リストでは、標準の項目リストで区切り記号を指定する場合と同様に、カスタムの区切り記号を指定できます。  たとえば、変換された項目リストを、既定のセミコロン \(;\) の代わりにコンマ \(,\) で区切るには、次の XML を使用します。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 たとえば、@\(RESXFile\) 項目リスト内の項目が `Form1.resx`、`Form2.resx`、および `Form3.resx` の場合、変換された一覧の出力は `Form1.resources`、`Form2.resources`、および `Form3.resources` となります。  
  
## 複数の修飾子の使用  
 変換式には複数の修飾子を含めることができます。修飾子は任意の順序で組み合わせることができ、繰り返すことができます。  次の例では、ファイルを含むディレクトリは名前が変更されますが、ファイルは元の名前および拡張子を保持します。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 たとえば、`RESXFile` 項目リスト内の項目が `Project1\Form1.resx`、`Project1\Form2.resx`、および `Project1\Form3.text` の場合、変換されたリストの出力は `Toolset\Form1.resx`、`Toolset\Form2.resx`、および `Toolset\Form3.text` となります。  
  
## 依存関係の分析  
 変換により、変換された項目のリストと元の項目のリストが一対一で割り当てられていることが保証されます。  したがって、ターゲットが入力の変換である出力を作成した場合、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は入力および出力のタイムスタンプを分析して、ターゲットをスキップ、ビルド、または部分的に再ビルドするかどうかを判断できます。  
  
 次の例の [Copy Task](../msbuild/copy-task.md) では、`BuiltAssemblies` 項目リストにあるすべてのファイルが、`Outputs` 属性の変換を使用して指定されている、タスクのコピー先フォルダーのファイルに割り当てられます。  `BuiltAssemblies` 項目リスト内のファイルが変更されると、変更されたファイルに対してのみ `Copy` タスクが実行され、その他のすべてのファイルはスキップされます。  依存関係分析の詳細と、変換の使用方法については、「[方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)」を参照してください。  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## 例  
  
### Description  
 次の例に、変換を使用する [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルを示します。  この例では、c:\\sub0\\sub1\\sub2\\sub3 ディレクトリに .xsd ファイルが 1 つだけあり、作業ディレクトリが c:\\sub0 であるものとします。  
  
### コード  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### コメント  
 この例を実行すると、次の出力が生成されます。  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## 参照  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [方法 : インクリメンタル ビルドを実行する](../msbuild/how-to-build-incrementally.md)