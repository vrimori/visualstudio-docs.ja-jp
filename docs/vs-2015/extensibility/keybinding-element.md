---
title: KeyBinding 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32dafc1b16282657db40531e34d1eccb02841481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780933"
---
# <a name="keybinding-element"></a>KeyBinding 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding 要素には、コマンドのキーボード ショートカットを指定します。  
  
 コマンドには、1 台または 2 の両方のキー バインドを使用して、それらに関連付けられていることができます。 1 つのキー バインドの例は、CTRL + S を**保存**コマンド。 2 つのキー バインドでは、コマンドをトリガーする 2 つの連続するキーの組み合わせが必要です。 2 つのキー バインドの例は、CTRL + K、ブックマークを設定するには、CTRL + K です。  
  
## <a name="syntax"></a>構文  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。|  
|ID|必須。|  
|エディター|必須。 エディターの GUID では、このショートカット キーがアクティブになる編集コンテキストを示します。 バインドのグローバル スコープの値は、"guidVSStd97 です"。|  
|key1|必須。 有効な値は、すべて判読の英数字と、2 桁の 16 進数値 0 x と VK_constants で前にします。|  
|mod1|任意。 Ctrl キー、ALT、およびスペースで区切られたシフトの任意の組み合わせ。|  
|key2|任意。 有効な値は、すべて判読の英数字と、2 桁の 16 進数値 0 x と VK_constants で前にします。|  
|mod2|任意。 Ctrl キー、ALT、およびスペースで区切られたシフトの任意の組み合わせ。|  
|エミュレーター|任意。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親||  
|注釈||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[KeyBindings 要素](../extensibility/keybindings-element.md)|KeyBinding 要素をグループ化し、他の KeyBindings グループ化します。|  
  
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
 [KeyBindings 要素](../extensibility/keybindings-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

