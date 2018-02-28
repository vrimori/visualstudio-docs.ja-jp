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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5628e3cca48799b602917fa1504479b46ee02dd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="processinfo"></a>PROCESS_INFO
プロセスに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
```csharp  
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
 フラグの組み合わせ、 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)のどのフィールドが埋められますを指定する列挙体です。  
  
 bstrFileName  
 プロセスの完全なパス名。 呼び出すことと同等、 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 、パラメーターを持つメソッド`GN_FILENAME`です。  
  
 bstrBaseName  
 ファイル名とプロセスの拡張機能。 呼び出すことと同等、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_BASENAME`です。  
  
 bstrTitle  
 1 つが存在する場合は、プロセスのタイトル。 呼び出すことと同等、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_TITLE`です。  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)プロセスを識別する構造体。 呼び出すことと同等、 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)メソッドです。  
  
 dwSessionId  
 このプロセスで実行されているデバッグ セッションの識別子。  
  
 bstrAttachedSessionName  
 接続されているセッションの名前です。 呼び出すことと同等、 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)メソッドです。  
  
 CreationTime  
 プロセスが作成された時刻。  
  
 フラグ  
 フラグの組み合わせ、 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)プロセスのプロパティを指定する列挙です。  
  
## <a name="remarks"></a>コメント  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)で塗り分けはメソッドです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)