---
title: IEnumDebugCodeContexts2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75765f714bd52d7e7b01eca15e451152ceba54a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980585"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
このインターフェイスは、または特定のプログラムまたはドキュメントをデバッグ セッションと関連付けられたコード コンテキストを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、プログラムでは、特定のテキストの位置のコード コンテキストの一覧または特定のドキュメント コンテキストのコード コンテキストの一覧を表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)プログラムのソース ドキュメント内の特定のテキストの位置のコード コンテキストの一覧を表す、このインターフェイスを取得します。  
  
 呼び出す[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)特定のソース ドキュメント内のすべてのコード コンテキストのリストを表す、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugCodeContexts2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|指定された数の列挙体シーケンス内のコードのコンテキストを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|指定された数の列挙体シーケンス内のコードのコンテキストをスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|列挙子では、コードのコンテキストの数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio 呼び出し[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)コード コンテキストの一覧を設定、ユーザーが選択できる場合に、次のステートメントを設定またはソース ファイルの逆アセンブルを表示します。 複数のコード コンテキストには、たとえば、C++ スタイルのテンプレートの複数のインスタンスがある場合が発生します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)