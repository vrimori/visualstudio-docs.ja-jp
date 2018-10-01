---
title: KeyBinding 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb8e0dca8293d5d5e853dde19e0c411cfd3e4e63
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495298"
---
# <a name="keybinding-element"></a>KeyBinding 要素
KeyBinding 要素には、コマンドのキーボード ショートカットを指定します。  
  
 コマンドには、1 台または 2 の両方のキー バインドを使用して、それらに関連付けられていることができます。 1 つのキー バインドの例は、 **Ctrl**+**S**の**保存**コマンド。 2 つのキー バインドでは、コマンドをトリガーする 2 つの連続するキーの組み合わせが必要です。 2 つのキー バインドの例は、 **Ctrl * +** K **、** Ctrl**+** K * は、ブックマークを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。|  
|ID|必須。|  
|エディター|必須。 エディターの GUID では、このショートカット キーがアクティブになる編集コンテキストを示します。 バインドのグローバル スコープの値は、"guidVSStd97 です"。|  
|key1|必須。 有効な値はすべて判読英数字、また 2 桁の 16 進値 0x と[VK_constants](/windows/desktop/inputdev/virtual-key-codes)します。|  
|mod1|任意。 任意の組み合わせ**Ctrl**、 **Alt**、および**Shift**スペースで区切られました。|  
|key2|任意。 有効な値はすべて判読英数字、また 2 桁の 16 進値 0x と[VK_constants](/windows/desktop/inputdev/virtual-key-codes)します。|  
|mod2|任意。 任意の組み合わせ**Ctrl**、 **Alt**、および**Shift**スペースで区切られました。|  
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
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
