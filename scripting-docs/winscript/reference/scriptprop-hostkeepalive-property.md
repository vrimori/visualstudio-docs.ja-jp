---
title: "SCRIPTPROP_HOSTKEEPALIVE プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE プロパティ
未解決の参照がある場合は、スクリプト エンジンが十分に機能して保存するかどうかを指定するために使用します。  
  
 `true`にこのプロパティを設定するに [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) を使用します。  このプロパティがに設定されている場合 `true`、スクリプト エンジンは、スクリプト エンジン自体への少なくとも 1 つがの未解決の参照がまたはの場合は、スクリプト エンジンを使用して作成された JavaScript オブジェクトへの `IDispatch` のポインターには完全には機能しません。  このプロパティが `true`に設定されている場合、[IActiveScript::Close](../../winscript/reference/iactivescript-close.md) または [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) のメソッドを使用して、スクリプト エンジンを閉じるか、またはリセットする必要があります。  スクリプト オブジェクトへの最後の参照のリリースでは、スクリプト エンジンをシャットダウンします。  
  
## 構文  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## 必要条件  
 このプロパティは [!INCLUDE[win8](../../javascript/includes/win8-md.md)]と、[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]の Internet Explorer 8 の 2707082 KB、または [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] または [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]の Internet Explorer 9 の 2722913 KB にインストール activscp.idl のバージョンにのみ表示されます。