---
title: テキスト マーカーを使用してレガシ API で |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ebef6593a019b09e7ee00cced56777d8488323f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141943"
---
# <a name="using-text-markers-with-the-legacy-api"></a>レガシ API でテキスト マーカーの使用
テキスト マーカーは、浮動表示に影響を与えるバッファー内のテキストの範囲とテキストの領域の動作です。 マーカーには、ブレークポイント、ブックマーク、波線、および読み取り専用領域が含まれます。 テキスト マーカーは、構文の色分け表示と基本的に異なります。 構文の色分けは、テキストの範囲に関連付けられている言語の構文を通信する簡単な方法です。 構文の色分けは、Windows 速度が重要である、画面を再描画するときに一般的に要求されます。 構文の色分けは、テキストの色のみを変更します。 テキスト マーカーは、その他の多くのテキストのプロパティを変更できます。 テキスト マーカーが「フローティング」および特別な動作を適用し、色分け表示します。  
  
 テキスト マーカーに関連付けられているパフォーマンスのオーバーヘッドが、原因、テキスト バッファーの多くのマーカーを作成できません。 それぞれのマーカーは、ユーザーが、バッファーの内容を編集するたびに更新されます。  
  
> [!NOTE]
>  ユーザーは、表示されるマーカーの種類がない、図形、スタイルの色を変更できます。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: 標準のテキストのマーカーの追加](../extensibility/how-to-add-standard-text-markers.md)|によって提供される標準のテキストのマーカーの種類を追加する方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト ビューにコア エディターです。|  
|[方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)|インスタンスを実装する方法について説明、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]赤色の波下線を使用して、エラーを示すために使用されるマーカー。|  
|[方法: カスタム テキスト マーカーを作成します。](../extensibility/how-to-create-custom-text-markers.md)|作成し、テキスト ビューに、カスタム テキスト マーカーの種類を追加する方法について説明します。|  
|[方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)|テキスト マーカーを追加する方法について説明します。|  
|[コア エディター内](../extensibility/inside-the-core-editor.md)|コア エディターの機能について説明し、コア エディターをカスタマイズする方法の詳細を提供します。|  
|[エディターの機能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|使用できる機能について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターです。|  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 エディターによって事前に定義または、VSPackage によって登録されているかどうかは、特定のテキスト マーカーの種類に関する情報を取得するための統一されたメカニズムを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 アクセスを提供し、2 次元座標を使用してテキスト バッファー内のテキスト マーカーの位置を調整します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 テキスト マーカーを管理するためのメソッドを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 コールバックを提供、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE およびテキスト マーカーの調整に使用されるその他のプロセスです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 を介して使用可能な機能を拡張、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>追加コールバックを提供することでインターフェイスです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 を介して使用可能な機能を拡張、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>追加コールバックを提供することでインターフェイスです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 その他のマーカーの種類が同じ色のセットを共有するかどうかを決定するマーカーの種類を有効にします。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 コア エディターでテキスト マーカーにコンテキストを提供します。 各テキスト マーカーの種類に対してコア エディターでは、IDE によって作成個別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>オブジェクト。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 マーカー グリフを含むドラッグ アンド ドロップ編集をサポートするために用意されているハンドラー。 グリフは、マーカーの位置を示すアイコンです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>テキストにその他の VSPackages にマーカーを提供するサービスからのインターフェイスです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 アクセスを提供し、1 次元座標を使用してテキスト バッファー内のテキスト マーカーの位置を調整します。 可能であれば、このインターフェイスは使用しないでください。