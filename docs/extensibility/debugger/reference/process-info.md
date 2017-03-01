---
title: "PROCESS_INFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 791686d7ab4516f5eb4da0642d97acb9df730f12
ms.lasthandoff: 02/22/2017

---
# <a name="processinfo"></a>PROCESS_INFO
プロセスの情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```c#  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>メンバー  
 フィールド  
 フラグの組み合わせ、 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)のどのフィールドが入力されたを指定する列挙値。  
  
 bstrFileName  
 プロセスの完全なパス名。 呼び出すことと同じ、 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 、パラメーターを持つメソッド`GN_FILENAME`します。  
  
 bstrBaseName  
 ファイル名とプロセスの拡張機能。 呼び出すことと同じ、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_BASENAME`します。  
  
 bstrTitle  
 存在する場合に、プロセスのタイトルです。 呼び出すことと同じ、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_TITLE`します。  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)プロセスを識別する構造体。 呼び出すことと同じ、 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)メソッドです。  
  
 dwSessionId  
 このプロセスが実行されているデバッグ セッションの識別子。  
  
 bstrAttachedSessionName  
 接続されているセッションの名前です。 呼び出すことと同じ、 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)メソッドです。  
  
 CreationTime  
 プロセスが作成された時刻。  
  
 フラグ  
 フラグの組み合わせ、 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)プロセスのプロパティを指定する列挙値。  
  
## <a name="remarks"></a>コメント  
 この構造体は、 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)メソッドでいっぱいになった場所。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
