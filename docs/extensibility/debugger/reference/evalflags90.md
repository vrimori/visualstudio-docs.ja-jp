---
title: EVALFLAGS90 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18f077bff6733467dbdf885be480fb4346edd513
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833181"
---
# <a name="evalflags90"></a>EVALFLAGS90
式の評価を制御するフラグの有効な値を列挙します。 この列挙体を拡張、 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列挙体。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>パラメーター  
 EVAL90_RETURNVALUE  
 存在する場合は、戻り値に評価することを指定します。  
  
 EVAL90_NOSIDEEFFECTS  
 副作用を許可しないことを指定します。  
  
 EVAL90_ALLOWBPS  
 ブレークポイントの停止を指定します。  
  
 EVAL90_ALLOWERRORREPORT  
 そのエラーを許可するホストにレポートを指定します。 主に、Internet Explorer でスクリプトに式の評価に使用します。  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 関数を呼び出す代わりに、アドレスとして評価される関数を強制的にします。  
  
 EVAL90_NOFUNCEVAL  
 関数が評価するを防ぎます。 たとえば、`int`式トークン`myExpression(int) + 10`します。 この関数は、アドレスとしてではない値を正しく評価できます。  
  
 EVAL90_NOEVENTS  
 セッション デバッグ マネージャー (SDM) または、IDE には式の評価中に発生するイベントを送信しないかを示すフラグです。  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 デザイン時の式の評価を有効にします。  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 暗黙的な変数の作成を許可します。  
  
 EVAL90_FORCE_EVALUATION_NOW  
 直ちに強制的に評価します。 これは、機能は、ユーザーの要求など、要求を処理するときに便利です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg90.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)