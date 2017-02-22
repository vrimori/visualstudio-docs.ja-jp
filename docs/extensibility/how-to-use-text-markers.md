---
title: "方法: テキストのマーカーを使用します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "従来のテキストのマーカーを使用してエディター [Visual Studio SDK]"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: テキストのマーカーを使用します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト マーカーが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> のオブジェクトの編集に適用できます。  
  
## 手順  
  
#### テキスト マーカーを適用するには  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> クラスのインスタンスを取得します。  
  
    > [!NOTE]
    >  コア エディターで編集する標準テキスト マーカーを明示的に適用する必要があるはずではありません。任意の文書に自動的に標準テキスト マーカーを適用します。  
  
2.  一つとして必要 `GUID` のテキスト マーカーの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> のメソッドを呼び出して必要なマーカーのマーカーの型 ID を取得します。  
  
    > [!NOTE]
    >  VSPackage またはテキスト マーカーを提供するサービス `GUID` を使用しないでください。  
  
3.  パラメーターとして <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> のメソッドの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> のメソッドまたはメソッドを <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> のテキストの指定した領域でテキスト マーカーを適用する呼び出しを呼び出しによって取得した ID のタイプ マーカーを使用します。  
  
#### テキスト マーカーの機能を追加するには  
  
1.  特殊事情のツールヒント特別なコンテキスト メニューまたはハンドラーなどテキスト マーカーの他の機能を追加することが望ましいこともあります。  そのため :  
  
2.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを実装するオブジェクトを作成します。  
  
3.  追加機能を指定する場合同じオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> のインターフェイスを実装する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを実装します。  
  
4.  作成したテキストの指定した領域でテキスト マーカーを適用するために使用される <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> メソッドまたはメソッドの呼び出しに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを渡します。  
  
5.  コンテキスト メニューのサポートをテキスト マーカーの領域に追加するときにメニューを作成する必要があります。  
  
     コンテキスト メニューを作成する方法の詳細については[コンテキスト メニュー](../extensibility/context-menus.md)" " を参照してください。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の環境では必要に応じて指定されたインターフェイスのメソッドメソッドなどの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>または <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> のメソッドを呼び出します。  
  
## 参照  
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: カスタム テキスト マーカーを作成](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)