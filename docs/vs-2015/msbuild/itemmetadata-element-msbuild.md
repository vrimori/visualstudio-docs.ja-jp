---
title: ItemMetadata 要素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0032b1798fea215169f801dd23beb8aa856effc5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537813"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata 要素 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ItemMetadata 要素 (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/itemmetadata-element-msbuild)します。  
  
  
ユーザー定義の項目メタデータのキーを格納します。項目メタデータの値が含まれます。 1 つの項目が、任意の数のメタデータ キー/値ペアを含むことができます。  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>構文  
  
```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Condition`|省略可能な属性です。<br /><br /> 評価する条件です。 詳細については、「[条件](../msbuild/msbuild-conditions.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|ビルド プロセスに対する入力を定義するユーザー定義の要素。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値は省略可能です。  
  
 このテキストは、項目メタデータの値を指定します。テキストまたは XML を使うことができます。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>例  
 次のコード例では、値が `fr` の `Culture` メタデータを項目 `CSFile` に追加する方法を示します。  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)



