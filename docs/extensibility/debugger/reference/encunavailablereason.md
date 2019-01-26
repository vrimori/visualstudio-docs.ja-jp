---
title: EncUnavailableReason |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f701a541077f3bdb53374deec0562fd68e5c7b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024371"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` 理由を表すを**エディット コンティニュ**は使用できません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 ENCUN_NONE  
 特定の理由がエディット コンティニュを使用できない原因です。  
  
 ENCUN_INTEROP  
 エディット コンティニュは相互運用機能の呼び出し中には使用できません。  
  
 ENCUN_SQLCLR  
 エディット コンティニュは共通言語ランタイム (CLR) を使用する SQL プロシージャの呼び出し中には使用できません。  
  
 ENCUN_MINIDUMP  
 エディット コンティニュはミニ ダンプの処理中には使用できません。  
  
 ENCUN_EMBEDDED  
 エディット コンティニュは埋め込みコードを処理するときに、使用できません。  
  
 ENCUN_ATTACH  
 エディット コンティニュを使用できないために、セッションが接続されていた、起動しないデバッガーによって。  
  
 ENCUN_WIN64  
 エディット コンティニュは 64 ビット Windows コードの処理中には使用できません。  
  
## <a name="remarks"></a>Remarks  
 この列挙体は内部使用のみで[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]します。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)と[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)カスタム ポートのサプライヤーによって実装されるメソッドは常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.idl  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)