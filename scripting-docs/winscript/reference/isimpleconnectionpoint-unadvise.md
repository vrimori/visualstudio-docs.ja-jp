---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
`ISimpleConnectionPoint::Advise` が以前に確立したアドバイザリ コネクションを終了します。  
  
## 構文  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### パラメーター  
 `dwCookie`  
 \[入力\]から返される `ISimpleConnectionPoint::Advise`、終了される接続のトークン。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 アドバイザリ コネクションを終了すると、コネクション ポイントは `ISimpleConnectionPoint::Advise` のメソッドの間に接続するために保存されたポインターの `Release` のメソッドを呼び出します。  `ISimpleConnectionPoint::Advise` 中にコネクション ポイントがアドバイズ シンク `QueryInterface`を呼び出すと、その呼び出しが行われた `AddRef` を反転させます。  
  
## 参照  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)