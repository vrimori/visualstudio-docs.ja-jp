---
title: Sdk 要素 (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24392fe34069025209f0e2c02e1231d1cbbe3397
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993275"
---
# <a name="sdk-element-msbuild"></a>Sdk 要素 (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト SDK を参照します。  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>構文  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  

### <a name="attributes"></a>属性  

|属性|説明|  
|---------------|-----------------|  
|`Name`|必須の属性です。<br /><br /> プロジェクト SDK の名前です。|  
|`Version`|省略可能な属性です。<br /><br /> プロジェクト SDK のバージョンです。|  

### <a name="child-elements"></a>子要素  
 なし。

### <a name="parent-elements"></a>親要素  

| 要素 | 説明 |
| - | - |
| [プロジェクト](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。 |

## <a name="see-also"></a>関連項目  
 [方法: MSBuild プロジェクト SDK の参照](../msbuild/how-to-use-project-sdk.md)   
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
