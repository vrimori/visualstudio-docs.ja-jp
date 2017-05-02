---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
シングル ステップ実行モードの言語のエンジンが呼び出し元に返されるするプロセス デバッグ マネージャーに通知します。  
  
## 構文  
  
```  
HRESULT StepOutComplete();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 言語のエンジンは、呼び出し元に戻る直前にシングル ステップ実行モードでこのメソッドを呼び出します。  プロセス デバッグ マネージャーは、最初の機会を中断することも、他のスクリプト エンジンをすべてこの通知する機会を使用します。  この方法は、言語間のステップのモードを実行する方法です。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)