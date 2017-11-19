---
title: "KeyBinding 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f620d895defbeeb3317f4a977db454a14ce3adc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="keybinding-element"></a>KeyBinding 要素
KeyBinding 要素には、コマンドのキーボード ショートカットを指定します。  
  
 コマンドには、1 台または 2 の両方のキー バインドを使用して、それらに関連付けられていることができます。 1 つのキー バインドの例は、CTRL + S の**保存**コマンド。 デュアル キー バインドでは、コマンドをトリガーする 2 つの連続するキーの組み合わせが必要です。 デュアル キー バインドの例は、CTRL + K、ブックマークを設定するには、CTRL + K です。  
  
## <a name="syntax"></a>構文  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須です。|  
|ID|必須です。|  
|エディター|必須です。 エディターの GUID では、次のキーボード ショートカットがアクティブになる編集コンテキストを示します。 バインディングのグローバル スコープの値は、"guidVSStd97"です。|  
|key1|必須です。 有効な値はすべて判読英数字、さらに 2 桁の 16 進値 0x と[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)です。|  
|mod1|省略可能です。 CTRL、alt キーを押し、およびスペースで区切られたシフトの任意の組み合わせ。|  
|key2|省略可能です。 有効な値はすべて判読英数字、さらに 2 桁の 16 進値 0x と[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)です。|  
|mod2|省略可能です。 CTRL、alt キーを押し、およびスペースで区切られたシフトの任意の組み合わせ。|  
|エミュレーター|省略可能です。|  
|状態|省略可能です。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親||  
|注釈||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[KeyBindings 要素](../extensibility/keybindings-element.md)|KeyBinding 要素をグループ化およびその他の KeyBindings グループ化します。|  
  
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
