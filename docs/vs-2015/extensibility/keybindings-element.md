---
title: KeyBindings 要素 |Microsoft Docs
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
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17845f85fd1634ad40d812d1b05a72ab15422b01
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282049"
---
# <a name="keybindings-element"></a>KeyBindings 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBindings 要素には、キー バインド要素とその他の KeyBindings グループがグループ化します。  
  
## <a name="syntax"></a>構文  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
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
|[KeyBinding 要素](../extensibility/keybinding-element.md)|コマンドのキーボード ショートカットを指定します。|  
|[キー バインド](../extensibility/keybindings-element.md)|KeyBinding 要素をグループ化し、他の KeyBindings グループ化します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|コマンドを表すすべての要素を定義します。|  
  
## <a name="example"></a>例  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>関連項目  
 [KeyBinding 要素](../extensibility/keybinding-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

