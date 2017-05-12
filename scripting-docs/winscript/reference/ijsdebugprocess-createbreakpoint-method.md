---
title: "IJsDebugProcess::CreateBreakPoint メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint メソッド
指定されたドキュメントの位置にブレークポイントを設定します。  
  
## 構文  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### パラメーター  
 `documentId`  
 \[入力\] IDebugDocumentText へのポインター。  
  
 `characterOffset`  
 \[入力\] ファイルの先頭からの文字オフセット。  
  
 `characterCount`  
 \[入力\] ブレークポイントを挿入するドキュメント テキストの長さ。  
  
 `isEnabled`  
 \[入力\] ブレークポイントが有効かどうかを指定します。  
  
 `ppDebugBreakPoint`  
 \[出力\] 作成されたブレークポイントを表すオブジェクト。  
  
## 戻り値  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [IJsDebugProcess インターフェイス](../../winscript/reference/ijsdebugprocess-interface.md)