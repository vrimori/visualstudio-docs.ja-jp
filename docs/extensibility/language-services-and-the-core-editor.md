---
title: "言語サービスとコア エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1528bc685577082df997535a680c372620821de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター
Visual Studio でのエディターは、言語サービスに頻繁に関連付けられます。 特には、言語サービスは、構文の色分け、ステートメント入力候補、IntelliSense、およびテキストの書式設定を提供します。  
  
## <a name="core-editors-and-document-data-objects"></a>コア エディターやドキュメント データ オブジェクト  
 コア エディターにアクセスすると、ドキュメント データおよびドキュメント ビュー オブジェクトは作成しません。 作成され、これら 2 つのオブジェクトを制御し、ファクトリの実装をエディターでの適切な呼び出しを行うことによってそれらへのハンドルを取得します。  
  
 詳細については、次を参照してください。[プロジェクトでファイルを開くエディターを決定する](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)です。  
  
## <a name="language-services-and-the-core-editor"></a>言語サービスとコア エディター  
 言語サービスを実装すると、ドキュメントのビューでデータを表示する方法を制御できます。 言語サービスは、情報とは、Visual C などの特定の言語に固有の動作を提供します。 テキスト バッファーをレジストリ キー、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors からこのファイル名拡張子に関連付けられた言語サービスを決定テキスト バッファーを作成して開いているドキュメントのファイル名拡張子を確認します。\\YourLanguageService {GUID} \Extensions です。 プロシージャを読み込み、標準的な VSPackage は、VSPackage を読み込んで、言語サービスのインスタンスを作成します。  
  
 基本的な言語サービスは、次の図に表示されます。  
  
 ![言語サービス モデル グラフィック](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
コア エディターと言語サービスのオブジェクト  
  
 コア エディター ドキュメント データ オブジェクトし、呼ばれ、バッファーにテキストで表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>オブジェクト。 ドキュメント ビュー オブジェクトし、呼ばれ、テキスト ビューで表される、<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>オブジェクト。 これら 2 つのオブジェクトは、コア エディターの統一されたビューを提供する言語サービスで共同作業します。 テキスト バッファーと、ドキュメント ウィンドウにテキスト ビューに表示される情報には、コード ウィンドウが呼び出されます。 コード ウィンドウのドキュメントは、コード ウィンドウ マネージャーによって管理されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [レガシ API を使用して、言語サービス コンテキストを提供します。](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense をホストしています。](../extensibility/intellisense-hosting.md)   
 [格納されている言語](../extensibility/contained-languages.md)   
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)