---
title: PROCESS_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7d99110511f9d126c2545ae2917c67afffb361f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767124"
---
# <a name="processinfo"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 フラグの組み合わせ、 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)フィールドが記入を指定する列挙体。  
  
 bstrFileName  
 プロセスの完全なパス名。 呼び出しに相当、 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 、パラメーターを持つメソッド`GN_FILENAME`します。  
  
 bstrBaseName  
 ファイル名とプロセスの拡張機能。 呼び出しに相当、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_BASENAME`します。  
  
 bstrTitle  
 存在する場合に、プロセスのタイトル。 呼び出しに相当、 `IDebugProcess2::Getname` 、パラメーターを持つメソッド`GN_TITLE`します。  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)プロセスを識別する構造体。 呼び出しに相当、 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)メソッド。  
  
 dwSessionId  
 このプロセスで実行されているデバッグ セッションの識別子。  
  
 bstrAttachedSessionName  
 接続されているセッションの名前。 呼び出しに相当、 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)メソッド。  
  
 CreationTime  
 プロセスが作成された時刻。  
  
 フラグ  
 フラグの組み合わせ、 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)プロセスのプロパティを指定する列挙体。  
  
## <a name="remarks"></a>Remarks  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)メソッドでいっぱいになった場所。  
  
## <a name="requirements"></a>必要条件  
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

