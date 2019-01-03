---
title: レガシ API を使用したテキスト マーカーの使用 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76c440c3c763b93c14ad03d9f48e6c977e9e5fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867002"
---
# <a name="using-text-markers-with-the-legacy-api"></a>レガシ API を使用したテキスト マーカーの使用
テキスト マーカーは、さまざまな浮動表示に影響を与えるバッファー内のテキストとテキストの範囲の動作です。 マーカーには、ブレークポイント、ブックマーク、波線の下線、および読み取り専用のリージョンが含まれます。 テキスト マーカーは、構文の色分け表示と基本的に異なります。 構文の色分けは、テキストの範囲に関連付けられている言語の構文を通信する簡単な方法を示します。 構文の色分け表示が要求されるの Windows の速度が重要な場合に、画面を再描画と一般にします。 構文の色分けは、テキストの色のみを変更します。 テキスト マーカーには、その他の多くのテキスト プロパティを変更できます。 テキスト マーカー「フローティング」して特別な動作を適用し、色分け表示します。  
  
 テキスト マーカーに関連付けられているパフォーマンス オーバーヘッドのため、テキスト バッファーの多くのマーカーを作成できません。 各マーカーは、ユーザーが、バッファーの内容を編集するたびに更新されます。  
  
> [!NOTE]
>  ユーザーは、表示されるマーカーの種類がない、図形、スタイルの色を変更できます。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)します。  
  
## <a name="related-topics"></a>関連トピック  
  
| Title | 説明 |
| - | - |
| [方法: 標準のテキスト マーカーを追加します。](../extensibility/how-to-add-standard-text-markers.md) | によって提供される標準のテキスト マーカーの種類を追加する方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト ビューにコア エディター。 |
| [方法: エラーのマーカーを実装します。](../extensibility/how-to-implement-error-markers.md) | インスタンスを実装する方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]赤い波線を使用してエラーを示すために使用されるマーカー。 |
| [方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md) | 作成し、テキスト ビューに、カスタム テキスト マーカーの種類を追加する方法について説明します。 |
| [方法: テキスト マーカーを使用します。](../extensibility/how-to-use-text-markers.md) | テキスト マーカーを追加する方法について説明します。 |
| [コア エディターの内部](../extensibility/inside-the-core-editor.md) | コア エディターの機能について説明し、コア エディターをカスタマイズする方法について詳しく説明します。 |
| [エディターの機能](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198) | 使用できる機能について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディター。 |
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 エディターによって定義済みまたは VSPackage によって登録されたかどうかは、特定のテキスト マーカーの種類に関する情報を取得するための統一メカニズムを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 アクセスを提供し、2 次元座標を使用してテキスト バッファー内のテキスト マーカーの位置を調整します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 テキスト マーカーを管理するためのメソッドを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 コールバックを提供します、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE およびテキスト マーカーの調整に使用されるその他のプロセス。  
  
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