---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "EVALFLAGS 列挙型"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式の評価を制御するフラグを指定します。  
  
## 構文  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## メンバー  
 EVAL\_RETURNVALUE  
 戻り値がある場合は評価することを指定します。  
  
 EVAL\_NOSIDEEFFECTS  
 副作用は使用できないことを指定します。  
  
 EVAL\_ALLOWBPS  
 停止したブレークポイントの Specifies。  
  
 EVAL\_ALLOWERRORREPORT  
 割り当てられるホストにエラー情報を指定します。  Internet Explorer でスクリプトの式の評価ではなく主に使用します。  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 強制は関数を呼び出す代わりにアドレスとして評価する方法について説明します。  
  
 EVAL\_NOFUNCEVAL  
 関数の評価されません。  たとえば式 `myExpression(int) + 10` の `int` トークンを検討してください。  この関数はアドレスでない値として正しく評価できます。  
  
 EVAL\_NOEVENTS  
 式の評価中に発生するイベントがデバッグ セッションの管理者や IDE に送信 \(SDM\) されないことを示すにはフラグを設定します。  
  
## 解説  
 これらのフラグは [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) と [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) のメソッドに引数として渡されます。  
  
 これらのフラグはまたはこれらのビットごとに組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)