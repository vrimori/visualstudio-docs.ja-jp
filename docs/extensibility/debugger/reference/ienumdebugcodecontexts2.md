---
title: "IEnumDebugCodeContexts2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cd6ead902a65a9f3e5e392b1b9dbeed135f326b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
このインターフェイスは、デバッグ セッションまたは特定のプログラムまたはドキュメントに関連付けられたコードのコンテキストを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、プログラムでは、特定のテキストの位置についてのコンテキストをコードの一覧または特定のドキュメントのコンテキストのコンテキストをコードの一覧を表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)プログラムのソース ドキュメント内の特定のテキストの位置についてのコンテキストをコードのリストを表す、このインターフェイスを取得します。  
  
 呼び出す[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)このインターフェイスを表す特定のソース ドキュメント内のすべてのコード コンテキストの一覧を取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugCodeContexts2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|列挙のシーケンス内のコードのコンテキストの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|列挙のシーケンス内のコードのコンテキストの指定した数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|列挙子では、コードのコンテキストの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 Visual Studio 呼び出し[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)コード コンテキストの一覧を作成するユーザーから選べますときに、次のステートメントを設定またはソース ファイルの逆アセンブルを表示します。 複数のコードのコンテキストには、たとえば、C++ スタイル テンプレートの複数のインスタンスがある場合が発生します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)