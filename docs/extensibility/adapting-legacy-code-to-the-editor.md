---
title: エディターにレガシ コードを改変. |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef1bce81e20772660a6074c15bd5dad494804373
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="adapting-legacy-code-to-the-editor"></a>エディターにレガシ コードを改変.
Visual Studio エディターには、既存のコード コンポーネントからアクセスできる多くの機能があります。 次の手順では、非 MEF コンポーネント、エディターの機能を使用するが、VSPackage ではなどを適合させる方法を示します。 アダプターを使用して、マネージとアンマネージ コードの両方で、エディターのサービスを取得する方法についても説明します。  
  
## <a name="editor-adapters"></a>エディターのアダプター  
 エディターのアダプター、または、shim もクラスとインターフェイスを公開しているエディター オブジェクトのラッパー、 <xref:Microsoft.VisualStudio.TextManager.Interop> API です。 たとえばエディター以外のサービス間で移動するアダプター、Visual Studio シェル コマンド、およびエディター サービスを使用することができます。 (これは Visual Studio で、エディターをホストする現在します。)また、アダプターには、Visual Studio で正しく動作するレガシのエディターおよび言語サービスの拡張が有効にします。  
  
## <a name="using-editor-adapters"></a>エディターのアダプターを使用します。  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>アダプターを作成するメソッドと新しいエディター インターフェイスと従来のインターフェイス間で切り替えるメソッドを提供します。  
  
 MEF コンポーネント パーツをこのサービスを使用している場合は、次のように、サービスをインポートできます。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 非 MEF コンポーネントでこのサービスを使用する場合は、このトピックの「「を使用して Visual Studio エディター サービスで、非 MEF コンポーネント」セクションに指示します。  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>エディターの新しい API と、レガシ API 間の切り替え  
 エディター オブジェクトと以前のインターフェイスを切り替えるには、次のメソッドを使用します。  
  
|メソッド|変換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|変換、<xref:Microsoft.VisualStudio.Text.ITextBuffer>を<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を<xref:Microsoft.VisualStudio.Text.ITextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を<xref:Microsoft.VisualStudio.Text.ITextBuffer>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|変換、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>を<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>を<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>です。|  
  
## <a name="creating-adapters"></a>アダプターを作成します。  
 従来のインターフェイスのアダプターを作成するのにには、次のメソッドを使用します。  
  
|メソッド|変換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>の指定された<xref:Microsoft.VisualStudio.Utilities.IContentType>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>の<xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>です。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> を作成します。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>アンマネージ コードでアダプターを作成します。  
 ローカルであるすべてのアダプター クラスが登録されている共同作成可能なを使用して、インスタンス化できます、`VsLocalCreateInstance()`関数。  
  
 すべてのアダプターで vsshlids.h ファイルで定義されている Guid を使用して作成します.Visual Studio SDK のインストールの \VisualStudioIntegration\Common\Inc\ フォルダーです。 VsTextBufferAdapter のインスタンスを作成するには、次のコードを使用します。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>マネージ コードでアダプターを作成します。  
 マネージ コードでは、アンマネージ コードの記述されるのと同じ方法で併置アダプターを作成できます。 作成し、アダプターと対話できる MEF サービスを使用することができます。 アダプターを取得するには、この方法は、数よりも共同作成するときによりきめ細かく制御できます。  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>IVsTextView のアダプターを作成するには  
  
1.  Microsoft.VisualStudio.Editor.dll への参照を追加します。 確認して`CopyLocal`に設定されている`false`です。  
  
2.  インスタンスを作成、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>、次のようにします。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  `CreateX()` メソッドを呼び出します。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>アンマネージ コードから直接、Visual Studio エディターを使用します。  
 Microsoft.VisualStudio.Platform.VSEditor 名前空間と Microsoft.VisualStudio.Platform.VSEditor.Interop 名前空間は、IVx * インターフェイスとして COM 呼び出し可能なインターフェイスを公開します。 たとえば、Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer インターフェイスが COM バージョンは、<xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイスです。 `IVxTextBuffer`、バッファー スナップショットへのアクセス、バッファーを修正で、バッファーでテキスト変更イベントをリッスンおよび追跡ポイントとの範囲を作成します。 次の手順にアクセスする方法を示します、`IVxTextBuffer`から、`IVsTextBuffer`です。  
  
#### <a name="to-get-an-ivxtextbuffer"></a>IVxTextBuffer を取得するには  
  
1.  IVx のインターフェイスの定義が VSEditor.h ファイルには.Visual Studio SDK のインストールの \VisualStudioIntegration\Common\Inc\ フォルダーです。  
  
2.  次のコードを使用してテキスト バッファーをインスタンス化、`IVsUserData->GetData()`メソッドです。 次のコードに`pData`へのポインター、`IVsUserData`オブジェクト。  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Visual Studio エディター サービスを非 MEF コンポーネントを使用してください。  
 MEF を使用していない既存のマネージ コード コンポーネントがあり、Visual Studio エディターのサービスを使用する場合は、ComponentModelHost VSPackage を含むアセンブリへの参照を追加し、その SComponentModel サービスを取得する必要があります。  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>非 MEF コンポーネントから Visual Studio エディターのコンポーネントを使用するには  
  
1.  Microsoft.VisualStudio.ComponentModelHost.dll アセンブリへの参照を追加します.Visual Studio のインストールの \Common7\IDE\ フォルダーです。 確認して`CopyLocal`に設定されている`false`です。  
  
2.  プライベートの追加`IComponentModel`を次のように、Visual Studio エディター サービスを使用するクラスのメンバーです。  
  
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
  
4.  その後、呼び出すことによって、Visual Studio エディターのサービスのいずれかを取得できます、`IComponentModel.GetService<T>()`サービスのメソッドです。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```