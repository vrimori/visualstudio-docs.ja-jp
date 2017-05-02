---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
アプリケーションへの手順であるコードによってアプリケーション プロセスのオブジェクトの作成を許可します。  
  
## 構文  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### パラメーター  
 `rclsid`  
 \[入力\]作成するオブジェクトのクラス ID \(CLSID\)。  
  
 `pUnkOuter`  
 `NULL`が集約オブジェクトの一部として、\[入力\]作成する。  それ以外 `pUnkOuter` は集約オブジェクトの `IUnknown` インターフェイス \(コントロールの `IUnknown`\) へのポインターです。  
  
 `dwClsContext`  
 \[入力\]実行中の実行可能コードのコンテキスト。  値は、列挙型 `CLSCTX`から取得されます。  
  
 `riid`  
 \[入力\]オブジェクトとの通信に使用されるインターフェイス ID。  
  
 `ppvObject`  
 \[出力\] `riid` で要求されたインターフェイス ポインターを受け取るポインター変数のアドレス。  正常に戻ると、\*`ppvObject` は要求されたインターフェイス ポインターが含まれます。  失敗に、\*`ppvObject` は `NULL`が含まれます。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `CoCreateInstance`このメソッドへのデリゲート。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)