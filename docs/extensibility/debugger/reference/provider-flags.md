---
title: PROVIDER_FLAGS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 340531f9c943052c1abd51203f3937ccd111e314
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126436"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
プログラム プロバイダーから取得するための必要なプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
typedef DWORD PROVIDER_FLAGS;  
```  
  
```csharp  
public enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
```  
  
## <a name="members"></a>メンバー  
 PFLAG_NONE  
 指定したフラグがありません。  
  
 PFLAG_REMOTE_PORT  
 呼び出し元が、別のコンピューターにプログラムの一覧[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]です。  
  
 PFLAG_DEBUGGEE  
 プロセスのこのインスタンスによって現在デバッグ中[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]です。  
  
 PFLAG_ATTACH_TODEBUGGEE  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] デバッグ中のプログラムにアタッチされていますが、それを起動できませんでした。  
  
 PFLAG_REASON_WATCH  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] イベントを監視します。  
  
 PFLAG_GET_PROGRAM_NODES  
 呼び出し元が、`ProgramNodes`のフィールド、 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)構造体。  
  
 PFLAG_GET_IS_DEBUGGER_PRESENT  
 呼び出し元が、`fIsTheDebuggerPresent`のフィールド、`PROVIDER_PROCESS_DATA`構造体。  
  
## <a name="remarks"></a>コメント  
 これらのフラグは、次のメソッドに渡されます。  
  
-   [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
-   [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
-   [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
 これらの値をビット単位と組み合わせて`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)