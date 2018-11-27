---
title: UsedCommands 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41e7f5002f8b80a7ecc0f14232c66316583ad0e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733869"
---
# <a name="usedcommands-element"></a>UsedCommands 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UsedCommands 要素には、UsedCommand 要素とその他の UsedCommands グループがグループ化します。  
  
 UsedCommands 要素は省略可能です。 場合は、パッケージの外部で定義されているコマンドを呼び出すことはありません、.vsct ファイルにこのセクションを含めることはありません。  
  
## <a name="syntax"></a>構文  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
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
|[UsedCommand 要素](../extensibility/usedcommand-element.md)|他のコードで実装されているコマンド。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|統合開発環境 (IDE) には、VSPackage を提供するコマンド (たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックスなど) を表すすべての要素を定義します。|  
  
## <a name="example"></a>例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>関連項目  
 [UsedCommand 要素](../extensibility/usedcommand-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

