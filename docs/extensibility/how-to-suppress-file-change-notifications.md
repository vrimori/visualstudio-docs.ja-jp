---
title: '方法: ファイル変更通知を抑制する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95821baec7f2f46a65e2ab0f0b0b78b0e397f2ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128773"
---
# <a name="how-to-suppress-file-change-notifications"></a>方法: ファイル変更通知を抑制します。
メッセージとダイアログ ボックスが表示テキスト バッファーを表す物理的なファイルが変更されると**を次の項目への変更を保存するか。** これは、ファイル変更通知と呼ばれます。 多くの変更に場合のファイルへ、ただし、このダイアログ ボックスを繰り返し表示はすぐに面倒な場合。  
  
 次の手順を使用してこのダイアログ ボックスを使用するプログラムで除外できます。 これにより、再読み込みできますファイルすぐに変更を保存するたびにユーザー入力を求める必要はありません。  
  
### <a name="to-suppress-file-change-notification"></a>ファイル変更通知を抑制するには  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>テキスト バッファー オブジェクトは、開いているファイルに関連付けられたを調べます。  
  
2.  直接、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクトを無視するメモリ内を監視しているファイルの変更を取得することによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>からインターフェイス、 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (ドキュメント データ) オブジェクト、および実装して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>メソッドを`fIgnore`パラメーター設定`true`です。  
  
3.  メソッドを呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイス、メモリ内の更新を<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>(ときに、フィールドは、コンポーネントに追加される) などのファイルの変更を持つオブジェクト。  
  
4.  保留中の編集中、ユーザーが持っているいずれかを考慮せず、変更内容をディスク上のファイルを更新します。  
  
     これにより、送信すると、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ファイルの監視を再開するオブジェクトの変更通知、メモリ内のテキスト バッファーには、その他のすべての保留中の編集だけでなく、生成した変更が反映されます。 ディスク上のファイルがによって生成された最新のコードを反映し、以前保存されたすべてのユーザーによる変更のコードのユーザーを編集します。  
  
5.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>に通知するメソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>ファイル変更通知を設定して監視を再開するオブジェクト、`fIgnore`パラメーターを`false`です。  
  
6.  ソース コード管理 (SCC) の場合と同様に、ファイルにいくつかの変更を加える場合は、ファイル変更通知を一時的に中断するグローバル ファイル変更サービスを指定する必要があります。  
  
     たとえば、ファイルを書き直して、タイムスタンプを変更すると、別のファイルの変更イベントとして各カウントする、書き換えおよび timestample 操作とファイル変更通知を中断する必要があります。 呼び出す必要はなくグローバル ファイル変更通知を有効にする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>メソッドです。  
  
## <a name="example"></a>例  
 ファイル変更通知を抑制する方法を次に示します。  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 場合に、SCC の場合と同様に、ファイルに複数の変更が含まれている場合は、アラート ドキュメント データ ファイルの変更の監視を再開する前にグローバル ファイル変更通知を再開する必要があります。