---
title: "Keybinding を割り当てる要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML スキーマ要素のショートカット キー"
  - "Keybinding を割り当てる要素 (VSCT XML スキーマ)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Keybinding を割り当てる要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Keybinding を割り当てる要素は、コマンドのキーボード ショートカットを指定します。  
  
 コマンドには、1 台または 2 の両方のキー バインドを使用して、それらに関連付けられていることができます。 1 つのキー バインドの例は、ctrl キーを押しながら S の **保存** コマンドです。 双方向のショートカット キーでは、コマンドをトリガーする 2 つ連続するキーの組み合わせが必要です。 デュアル キー バインドの例は、CTRL \+ K、ブックマークを設定するには、CTRL \+ K です。  
  
## 構文  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。|  
|ID|必須です。|  
|エディター|必須です。 エディターの GUID では、次のキーボード ショートカットがアクティブになる編集コンテキストを示します。 バインディングのグローバル スコープの値は、"guidVSStd97"です。|  
|key1|必須です。 有効な値には、すべて判読英数字、さらに 2 桁の 16 進値が前に 0 の x と VK\_constants が含まれます。|  
|mod1|省略可能です。 Ctrl キー、alt キーを押し、およびスペースで区切ってシフトの任意の組み合わせ。|  
|key2|省略可能です。 有効な値には、すべて判読英数字、さらに 2 桁の 16 進値が前に 0 の x と VK\_constants が含まれます。|  
|mod2|省略可能です。 Ctrl キー、alt キーを押し、およびスペースで区切ってシフトの任意の組み合わせ。|  
|エミュレーター|省略可能です。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|親||  
|注釈||  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[ショートカット キーの要素](../extensibility/keybindings-element.md)|Keybinding を割り当てる要素をグループ化し、その他のショートカット キーのグループ化します。|  
  
## 使用例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 参照  
 [ショートカット キーの要素](../extensibility/keybindings-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)