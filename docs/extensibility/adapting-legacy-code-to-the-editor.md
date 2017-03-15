---
title: "エディターにレガシ コードを改変 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - レガシー アダプター"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# エディターにレガシ コードを改変
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio エディターでは、既存のコード コンポーネントからアクセスできる多くの機能を備えています。 次の手順では、エディターの機能を使用する、VSPackage など、非 MEF コンポーネントを調整する方法を示しています。 アダプターを使用して、マネージ コードとアンマネージの両方のコードで、エディターのサービスを取得する方法についても説明します。  
  
## エディターのアダプター  
 エディターのアダプター、または、shim もクラスとのインターフェイスを公開するエディター オブジェクトのラッパー、 <xref:Microsoft.VisualStudio.TextManager.Interop> API です。 たとえばエディター以外のサービス間で移動するアダプター、Visual Studio シェル コマンド、およびエディター サービスを使用することができます。 \(これは Visual Studio で、エディターが現在ホストされるしくみです。\) また、アダプターには、Visual Studio で正しく動作する従来のエディターと言語サービスの拡張が有効にします。  
  
## エディターのアダプターを使用します。  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> エディターの新しいインターフェイスと従来のインターフェイスを切り替える方法ともアダプターを作成するメソッドを提供します。  
  
 MEF コンポーネントのパートでこのサービスを使用している場合は、次のように、サービスをインポートできます。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 非 MEF コンポーネントでこのサービスを使用する場合は、このトピックの後半「を使用して Visual Studio エディターのサービスで、非 MEF コンポーネント」セクションに指示します。  
  
## エディターの新しい API とレガシ API 間の切り替え  
 Editor オブジェクトと以前のインターフェイス間を切り替えるには、次のメソッドを使用します。  
  
|メソッド|変換|  
|----------|--------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|変換、 <xref:Microsoft.VisualStudio.Text.ITextBuffer> に、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|変換、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> に、 <xref:Microsoft.VisualStudio.Text.ITextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|変換、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> に、 <xref:Microsoft.VisualStudio.Text.ITextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|変換、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> に、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|変換、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> に、 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>です。|  
  
## アダプターを作成します。  
 次のメソッドを使用すると、従来のインターフェイス用にアダプターを作成できます。  
  
|メソッド|変換|  
|----------|--------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|作成、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 、指定された <xref:Microsoft.VisualStudio.Utilities.IContentType>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|作成、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> の <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> を作成します。|  
  
## アンマネージ コードでアダプターを作成します。  
 ローカルですべてのアダプター クラスが登録されている共同作成可能な型を使用して、インスタンス化できます、 `VsLocalCreateInstance()` 関数です。  
  
 すべてのアダプターが vsshlids.h ファイルで定義されている Guid を使用して作成された、.Visual Studio SDK のインストールの \\VisualStudioIntegration\\Common\\Inc\\ フォルダーです。 VsTextBufferAdapter のインスタンスを作成するには、次のコードを使用します。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## マネージ コードでアダプターを作成します。  
 マネージ コードでは、アンマネージ コードの記述されるのと同じ方法で共存アダプターを作成できます。 またを作成し、アダプターと対話できる MEF サービスを使用することができます。 アダプターを取得するには、この方法は、数よりも共同作成するときをよりきめ細かく制御できます。  
  
#### IVsTextView のアダプターを作成するには  
  
1.  Microsoft.VisualStudio.Editor.dll への参照を追加します。 確認して `CopyLocal` に設定されている `false`します。  
  
2.  インスタンスを作成、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, 、次のようにします。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  `CreateX()` メソッドを呼び出します。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## アンマネージ コードから直接 Visual Studio エディターを使用します。  
 Microsoft.VisualStudio.Platform.VSEditor 名前空間および Microsoft.VisualStudio.Platform.VSEditor.Interop 名前空間は、IVx \* インターフェイスとして COM 呼び出し可能なインターフェイスを公開します。 たとえば、Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer インターフェイスには、COM バージョンの <xref:Microsoft.VisualStudio.Text.ITextBuffer> インターフェイスです。`IVxTextBuffer`, 、バッファーのスナップショットにアクセスする、バッファーを変更、そのバッファーに対してテキスト変更イベントをリッスンおよび追跡ポイントとの範囲を作成します。 次の手順にアクセスする方法を説明する、 `IVxTextBuffer` から、 `IVsTextBuffer`です。  
  
#### IVxTextBuffer を取得するには  
  
1.  IVx のインターフェイスの定義は VSEditor.h ファイルには.Visual Studio SDK のインストールの \\VisualStudioIntegration\\Common\\Inc\\ フォルダーです。  
  
2.  次のコードをテキスト バッファーをインスタンス化を使用して、 `IVsUserData->GetData()` メソッドです。 次のコードに `pData` へのポインター、 `IVsUserData` オブジェクトです。  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## Visual Studio エディター サービスを非 MEF コンポーネントを使用してください。  
 MEF を使用しない既存のマネージ コード コンポーネントがあり、Visual Studio エディターのサービスを使用する場合は、ComponentModelHost VSPackage を含むアセンブリへの参照を追加し、SComponentModel サービスを取得します。  
  
#### 非 MEF コンポーネントから Visual Studio エディターのコンポーネントを使用するには  
  
1.  Microsoft.VisualStudio.ComponentModelHost.dll アセンブリへの参照を追加します.Visual Studio のインストールの \\Common7\\IDE\\ フォルダーです。 確認して `CopyLocal` に設定されている `false`します。  
  
2.  追加のプライベート `IComponentModel` を次のように Visual Studio エディターのサービスを使用するクラスのメンバーです。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  コンポーネントの初期化メソッドでコンポーネント モデルのインスタンスを作成します。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  その後を呼び出して Visual Studio エディターのサービスのいずれかを取得することができます、 `IComponentModel.GetService<T>()` サービスのメソッドです。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```