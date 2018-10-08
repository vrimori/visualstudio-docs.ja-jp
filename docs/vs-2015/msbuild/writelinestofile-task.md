---
title: WriteLinesToFile タスク | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0256ea6242a01cd8e18017889dc450bc60e6fc82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546687"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[WriteLinesToFile タスク](https://docs.microsoft.com/visualstudio/msbuild/writelinestofile-task)します。  
  
  
指定したアイテムのパスを指定したテキスト ファイルに書き込みます。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `WriteLinestoFile` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`File`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 項目を書き込むファイルを指定します。|  
|`Lines`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> ファイルに書き込む項目を指定します。|  
|`Overwrite`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、タスクはファイル内の既存のコンテンツをすべて上書きします。|  
|`Encoding`|省略可能な `String` 型のパラメーターです。<br /><br /> 文字エンコードを選択します。たとえば、"Unicode" を選択します。  「<xref:System.Text.Encoding>」も参照してください。|  
  
## <a name="remarks"></a>Remarks  
 `Overwrite` が `true` の場合、新しいファイルを作成し、内容をそのファイルに書き込んだ後、ファイルを閉じます。 既存のターゲット ファイルは上書きされます。 `Overwrite` が `false` の場合、ファイルにコンテンツを追加します。ターゲット ファイルがまだ存在しない場合は、ファイルを作成します。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`WriteLinesToFile` タスクを利用し、`MyTextFile` 項目コレクションにより指定されたファイルに、`MyItems` 項目コレクションの項目のパスを書き込みます。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



