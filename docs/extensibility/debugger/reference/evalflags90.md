---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90 列挙型"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式の評価を制御するフラグの有効な値を列挙します。  この列挙体は [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙型を拡張します。  
  
## 構文  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```c#  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### パラメーター  
 EVAL90\_RETURNVALUE  
 戻り値がある場合は評価することを指定します。  
  
 EVAL90\_NOSIDEEFFECTS  
 副作用は使用できないことを指定します。  
  
 EVAL90\_ALLOWBPS  
 停止したブレークポイントの Specifies。  
  
 EVAL90\_ALLOWERRORREPORT  
 割り当てることをホストがエラー レポート指定します。  Internet Explorer でスクリプトの式の評価ではなく主に使用します。  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 関数を呼び出す代わりにアドレスとして強制的に評価される関数。  
  
 EVAL90\_NOFUNCEVAL  
 関数の評価されません。  たとえば式 `myExpression(int) + 10` の `int` トークンを検討してください。  この関数はアドレスでない値として正しく評価できます。  
  
 EVAL90\_NOEVENTS  
 式の評価中に発生するイベントがデバッグ セッションの管理者や IDE に送信 \(SDM\) されないことを示すにはフラグを設定します。  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 デザイン時の式の評価を可能にします。  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 暗黙的な変数を作成できます。  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 評価をすぐに実行されます。  これはユーザー要求などその要求を処理する場合に便利です。  
  
## 必要条件  
 ヘッダー : Msdbg90.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)