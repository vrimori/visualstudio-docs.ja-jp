---
title: "従来の言語サービスのモデル | Microsoft Docs"
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
  - "モデルを言語サービス"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスのモデル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

言語サービスは特定の言語の要素と機能を定義しその言語固有の情報をエディターを提供するために使用されます。  たとえば構文の色指定をサポートする言語の要素とキーワードを指定する必要があります。  
  
 言語サービスはエディターおよびエディターを含むビューでテキスト バッファーのマネージと緊密に使用します。  \[入力\] オプション ENT0ENT な Microsoft IntelliSense は言語サービスで提供される機能の一例です。  
  
## 最小限の言語サービス  
 基本的な言語サービスは2 種類のオブジェクトが含まれます :  
  
-   *言語サービスは*  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> のインターフェイスを実装します。  言語サービスの名前はファイル名拡張子ウィンドウ マネージャーとコード colorizer を含む言語に関する情報があります。  
  
-   *colorizer は*  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> のインターフェイスを実装します。  
  
 次の概念的な描画は基本的な言語サービスのモデルを示します。  
  
 ![言語サービス モデル グラフィック](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本的な言語サービスのモデル  
  
 ドキュメント ウィンドウはエディターこの場合 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコア エディター  *ドキュメント*  の  *ビューを*  ホストします。  ドキュメントのビューとテキスト バッファーがエディターによって所有されます。  これらのオブジェクトは *コード ウィンドウと*  呼ばれる特殊なドキュメント ウィンドウを使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を使用します。  コード ウィンドウはIDE によって作成および管理される <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> のオブジェクトに含まれています。  
  
 特定の拡張子を持つファイルが読み込まれるとその拡張子に関連付けられている言語サービスを選択し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> のメソッドを呼び出しコード ウィンドウを渡します。  言語サービスは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> のインターフェイスを実装する  *コード ウィンドウ マネージャーを*  返します。  
  
 次の表はモデル オブジェクトの概要を示します。  
  
|コンポーネント|Object|Function|  
|-------------|------------|--------------|  
|テキスト バッファー|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode テキスト ストリームの読み取り \/ 書き込み。  テキストが他のエンコーディングを使用することもできます。|  
|コード ウィンドウ|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|一つ以上のテキスト ビューを含むドキュメント ウィンドウ。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] がマルチ ドキュメント インターフェイス モードの場合\(MDI\) コード ウィンドウが MDI 子です。|  
|テキスト ビュー|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|ユーザーがキーボードとマウスを使用してテキストを移動し表示するウィンドウ。  ビューではテキスト エディターとしてユーザーに表示されます。  通常エディター ウィンドウには\[出力\] ウィンドウと \[イミディエイト\] ウィンドウでテキスト ビューを使用できます。  またコード ウィンドウ内の一つ以上のテキスト ビューを構成できます。|  
|テキスト マネージャー|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> のポインターを取得 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> サービスによって管理|前に説明したすべてのコンポーネントによって共有される共通の情報を保持するコンポーネント。|  
|言語サービス|実装に依存 ; <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> を実行します。|構文言語固有の情報を強調表示するエディター オブジェクトに対するステートメント入力候補かっこの一致。|  
  
## 参照  
 [ドキュメント データとカスタム エディターでドキュメント ビュー](../../extensibility/document-data-and-document-view-in-custom-editors.md)