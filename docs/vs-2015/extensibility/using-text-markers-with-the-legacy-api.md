---
title: レガシ API を使用したテキスト マーカーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f863571672c42f63912629844fd72d8c92ca8400
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263667"
---
# <a name="using-text-markers-with-the-legacy-api"></a>レガシ API を使用したテキスト マーカーの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキスト マーカーは、さまざまな浮動表示に影響を与えるバッファー内のテキストとテキストの範囲の動作です。 マーカーには、ブレークポイント、ブックマーク、波線の下線、および読み取り専用のリージョンが含まれます。 テキスト マーカーは、構文の色分け表示と基本的に異なります。 構文の色分けは、テキストの範囲に関連付けられている言語の構文を通信する簡単な方法を示します。 構文の色分け表示が要求されるの Windows の速度が重要な場合に、画面を再描画と一般にします。 構文の色分けは、テキストの色のみを変更します。 テキスト マーカーには、その他の多くのテキスト プロパティを変更できます。 テキスト マーカー「フローティング」して特別な動作を適用し、色分け表示します。  
  
 テキスト マーカーに関連付けられているパフォーマンス オーバーヘッドのため、テキスト バッファーの多くのマーカーを作成できません。 各マーカーは、ユーザーが、バッファーの内容を編集するたびに更新されます。  
  
> [!NOTE]
>  ユーザーは、表示されるマーカーの種類がない、図形、スタイルの色を変更できます。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)します。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[方法: 標準のテキスト マーカーを追加する](../extensibility/how-to-add-standard-text-markers.md)|によって提供される標準のテキスト マーカーの種類を追加する方法について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]テキスト ビューにコア エディター。|  
|[方法: エラー マーカーを実装する](../extensibility/how-to-implement-error-markers.md)|インスタンスを実装する方法について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]赤い波線を使用してエラーを示すために使用されるマーカー。|  
|[方法: カスタム テキスト マーカーを作成する](../extensibility/how-to-create-custom-text-markers.md)|作成し、テキスト ビューに、カスタム テキスト マーカーの種類を追加する方法について説明します。|  
|[方法: テキスト マーカーを使用する](../extensibility/how-to-use-text-markers.md)|テキスト マーカーを追加する方法について説明します。|  
|[コア エディターの内部](../extensibility/inside-the-core-editor.md)|コア エディターの機能について説明し、コア エディターをカスタマイズする方法について詳しく説明します。|  
|[エディターの機能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|使用できる機能について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]のコア エディター。|  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 エディターによって定義済みまたは VSPackage によって登録されたかどうかは、特定のテキスト マーカーの種類に関する情報を取得するための統一メカニズムを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 アクセスを提供し、2 次元座標を使用してテキスト バッファー内のテキスト マーカーの位置を調整します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 テキスト マーカーを管理するためのメソッドを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 コールバックを提供します、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE およびテキスト マーカーの調整に使用されるその他のプロセス。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 使用可能な機能を拡張して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>追加コールバックを提供することでインターフェイス。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 使用可能な機能を拡張して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>追加コールバックを提供することでインターフェイス。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 その他のマーカーの種類が同じ色のセットを共有するかどうかを判断するマーカーの種類を有効にします。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 テキスト マーカーのコア エディターのコンテキストを提供します。 コア エディター内にあるテキスト マーカー種類ごとに、IDE によって作成個別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>オブジェクト。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 マーカー グリフを含むドラッグ アンド ドロップの編集はサポートされているハンドラー。 グリフは、マーカーの位置を示すアイコンです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>インターフェイスから他の Vspackage にマーカーをテキストを提供するサービスです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 アクセスを提供し、1 次元の座標を使用してテキスト バッファー内のテキスト マーカーの位置を調整します。 可能である場合、このインターフェイスを使用することはしません。

