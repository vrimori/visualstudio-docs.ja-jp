---
title: VisibilityConstraints 要素 |Microsoft Docs
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
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9fd6d6968984f0640dd73067c286a4259ade6745
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547117"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[VisibilityConstraints 要素](https://docs.microsoft.com/visualstudio/extensibility/visibilityconstraints-element)します。  
  
VisibilityConstraints 要素は、コマンドとツールバーのグループの静的な可視性を判断します。 可視性がによって制御される最初の[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]VSPackage を読み込むことがなく、統合開発環境 (IDE) です。  
  
## <a name="syntax"></a>構文  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VisibilityItem 要素](../extensibility/visibilityitem-element.md)|コマンドとツールバーの静的な可視性を判断します。|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|コマンドとツールバーのグループの静的な可視性を判断します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|IDE に VSPackage を提供するコマンド (たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックスなど) を表すすべての要素を定義します。|  
  
## <a name="example"></a>例  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>関連項目  
 [VisibilityItem 要素](../extensibility/visibilityitem-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

