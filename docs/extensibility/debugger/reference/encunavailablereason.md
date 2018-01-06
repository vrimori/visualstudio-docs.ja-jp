---
title: "EncUnavailableReason |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EncUnavailableReason
helpviewer_keywords: EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c057b01c07bd3a2ae9466dc394676fe553fe14d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`理由を表すを**エディット コンティニュ**は使用できません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
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
 特定の理由がなぜエディット コンティニュは使用できません。  
  
 ENCUN_INTEROP  
 エディット コンティニュは相互運用機能の呼び出し中には使用できません。  
  
 ENCUN_SQLCLR  
 エディット コンティニュは共通言語ランタイム (CLR) を使用する SQL プロシージャ呼び出しでは使用できません。  
  
 ENCUN_MINIDUMP  
 エディット コンティニュは、ミニ ダンプを処理中には使用できません。  
  
 ENCUN_EMBEDDED  
 エディット コンティニュは埋め込みコードを処理するときに、使用できません。  
  
 ENCUN_ATTACH  
 エディット コンティニュは使用できない、セッションにアタッチされているために起動していない、デバッガーによってです。  
  
 ENCUN_WIN64  
 エディット コンティニュは 64 ビット Windows コードの処理中には使用できません。  
  
## <a name="remarks"></a>コメント  
 この列挙体は内部使用のみで[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]です。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)と[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)カスタム ポート業者によって実装されるメソッドを常に返します`E_NOTIMPL`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)