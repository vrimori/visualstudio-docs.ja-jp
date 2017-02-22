---
title: "方法: 項目リストをコンマ区切りで表示する | Microsoft Docs"
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
  - "MSBuild, 書式設定 (項目のコレクションを)"
  - "MSBuild, 区切る (項目をセミコロンで)"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法: 項目リストをコンマ区切りで表示する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) で項目リストを使用する場合、項目リストの内容を見やすく表示したい場合があります。  あるいは、項目のリストを特殊な区切り記号文字列で区切って指定しなければならないタスクもあります。  どちらの場合も、項目リストに対して区切り記号文字列を指定できます。  
  
## リスト項目をコンマで区切る  
 既定では、リスト内の項目は [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] によりセミコロンで区切られます。  たとえば、次の値を持つ `Message` 要素があるとします。  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 `@(TXTFile)` 項目リストに App1.txt、App2.txt、App3.txt という項目が含まれる場合、メッセージは次のように表示されます。  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 既定の動作は、他の区切り記号を指定することによって変更できます。  項目リストの区切り記号を指定するための構文を次に示します。  
  
 `@(ItemListName, '<separator>')`  
  
 区切り記号は 1 文字だけでも、文字列でもかまいません。単一引用符で囲んで指定します。  
  
#### 項目間にコンマとスペースを挿入するには  
  
-   次のような項目表記を使用します。  
  
     `@(TXTFile, ', ')`  
  
## 使用例  
 この例では、[Exec](../msbuild/exec-task.md) タスクによって findstr ツールを実行し、Phrases.txt ファイルから指定された文字列を検索します。  findstr コマンドでは、**\/c:** スイッチでリテラル検索文字列が指定されます。そのため、項目の区切り記号 `/c:` を `@(Phrase)` 項目リスト内の項目の間に挿入しています。  
  
 この例は、コマンド ラインから次のようなコマンドを実行することに相当します。  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## 参照  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [項目](../msbuild/msbuild-items.md)