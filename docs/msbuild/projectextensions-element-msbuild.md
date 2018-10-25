---
title: ProjectExtensions 要素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0057d51256f9cddff7c30056d4c669e9f2f2dd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895458"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 要素 (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルに、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 以外の情報を含めることを可能にします。 `ProjectExtensions` 要素内のすべてのものは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] によって無視されます。  

 \<Project>  
 \<ProjectExtensions >  

## <a name="syntax"></a>構文  

```xml  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  

## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  

### <a name="attributes"></a>属性  
 なし  

### <a name="child-elements"></a>子要素  
 なし  

### <a name="parent-elements"></a>親要素  

| 要素 | 説明 |
| - | - |
| [プロジェクト](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルの必須のルート要素です。 |

## <a name="remarks"></a>コメント  
 `ProjectExtensions` 要素は [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトで1 つだけ使用できます。  

## <a name="example"></a>例  
 次のコード例は、`ProjectExtensions` 要素に格納されている統合開発環境の情報を示します。  

```xml  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  

## <a name="see-also"></a>関連項目  
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
