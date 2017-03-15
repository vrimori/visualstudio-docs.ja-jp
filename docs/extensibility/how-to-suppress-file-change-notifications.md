---
title: "方法: ファイル変更通知を抑制します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] のレガシ ファイル変更通知を抑制します。"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 方法: ファイル変更通知を抑制します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト バッファーを表す物理ファイルが変更されるとメッセージ **\*\*\* Do you want to save changes to the following items? \*\*\*** を持つダイアログ ボックスの表示これはファイル変更通知と呼ばれます。  多数の変更がファイルにあるかメニューを何度も表示されます。このダイアログ ボックスは迷惑になることがあります。  
  
 次の手順を使用してプログラムでこのダイアログ ボックスを表示できます。  これによりユーザーが変更を保存するたびにメッセージを表示せずにファイルをすぐに再読み込みできます。  
  
### ファイル変更通知は表示されません。  
  
1.  のテキスト バッファーのオブジェクトが開いているファイルに関連付けられているかを判断するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> のメソッドを呼び出します。  
  
2.  無視しメモリの `true` への `fIgnore` のパラメーターをに設定して <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> メソッドの実装を <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(ドキュメント\) のデータ オブジェクトから <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> のインターフェイスを取得して監視ファイルの変更を指示します。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のオブジェクト。  
  
3.  フィールドをコンポーネントに追加されている場合\) ファイルの変更によるメモリの <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のオブジェクトを更新するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> インターフェイスのメソッドを呼び出します \(など\)。  
  
4.  ユーザーが処理中である可能性がある保留中の編集を考慮することなく変更を含むディスク上のファイルを更新します。  
  
     この方法でファイル変更通知の再開の監視に <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のオブジェクトを使用するとメモリのテキスト バッファーは生成した他の保留中の変更すべて編集を反映します。  ディスク上のファイルによって生成する最新のコードをユーザーが編集されたコードのユーザーによって以前に保存した反映します。  
  
5.  `false` に `fIgnore` のパラメーターを設定することでファイル変更通知の再開の監視に <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> のオブジェクトに通知するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> のメソッドを呼び出します。  
  
6.  ファイルへの変更を行う場合は\(SCC\) ソース・コード管理の場合はグローバル ファイルの変更のサービスを一時ファイル変更通知を中断するように指示する必要があります。  
  
     たとえばファイルを書き換えタイムスタンプを変更する場合は関数を書き直したと timestample の操作として別ファイルの変更イベントとして各数値ファイル変更通知が中断する必要があります。  グローバル ファイルの変更通知を有効にするには<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> のメソッドを呼び出す必要があります。  
  
## 使用例  
 次のファイル変更通知を抑制する方法を示します。  
  
```cpp#  
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
  
## 信頼性の高いプログラミング  
 ケースはファイルへの複数の変更が含まれる場合はSCCその場合のようにファイルの変更を監視を再開するにはドキュメント データの通知前にグローバル ファイルの変更通知を再開する必要があります。