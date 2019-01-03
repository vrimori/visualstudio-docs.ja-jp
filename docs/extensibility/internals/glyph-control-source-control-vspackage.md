---
title: グリフ管理 (ソース管理 VSPackage) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e432e045a55593f0967c7805323785cfc6acaa7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870048"
---
# <a name="glyph-control-source-control-vspackage"></a>グリフ管理 (ソース管理 VSPackage)
ソース管理 Vspackage を使用できる高度な統合の一部をソース管理下にある項目の状態を示すために、独自のグリフを表示する機能があります。  
  
## <a name="levels-of-glyph-control"></a>コントロールのグリフのレベル  
 状態のグリフが例では、表示されるときに、項目の現在の状態を示すアイコン**ソリューション エクスプ ローラー**または**クラス ビュー**します。 ソース管理 VSPackage では、2 つのレベルのグリフの制御を実行できます。 定義済みセットによって提供されるグリフのグリフの選択を制限することができます、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE、またはそれが表示されるグリフのカスタム セットを定義できます。  
  
### <a name="default-set-of-glyphs"></a>既定のグリフのセット  
 内の項目に関連付けられている状態のグリフを決定する**ソリューション エクスプ ローラー**、プロジェクトを使ってソール コントロールからの状態のグリフの要求、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>します。 ソース管理 VSPackage は、IDE によって提供される定義済みのグリフに限定するグリフの選択を保持すること可能性があります。 この場合、VSPackage 渡しますで定義されているグリフ列挙型を表す値の配列*vsshell.idl*します。 詳細については、「 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> 」を参照してください。 これは、グリフ、南京錠のグリフにチェックインとチェック アウトのグリフのチェック マークなど、IDE によって設定の定義済みセット。  
  
### <a name="custom-set-of-glyphs"></a>グリフのカスタム セット  
 ソース管理 VSPackage がインストールされているときに、一意のルック アンド フィールを独自のグリフを使用できます。 新しいソース管理 VSPackage がアクティブな場合は、独自のグリフ場合でも、以前のソース管理 VSPackage がまだ読み込まれて使用を開始することが、非アクティブなが必要です。 このモードでソース管理 VSPackage でも使用できます、既存のアイコンを参照するくださいと一貫性を維持するために[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]選択した場合。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>サービスは、インターフェイスをサポートしている<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>これにより、VSPackage をオプションで実装され、ide に求められますが。 IDE で、要求が発行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]現在登録されているソース管理 VSPackage からこのインターフェイスを取得する順番を試みます。 カスタム グリフの IDE の要求が成功した登録済みの VSPackage で、インターフェイスが存在する場合それ以外の場合、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は一連の既定のグリフを使用します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>メソッドで使用される[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の状態を示すさまざまなソース管理のイメージの一覧を取得します。 ソース管理 VSPackage は、IDE にカスタムのグリフのイメージ リストを識別するハンドルを返します。 IDE では、この時点でイメージ リストのコピーを作成し、表示するグリフを選択するために後で使用します。 新しいインターフェイスがサポートされていない場合、または`IVsSccGlyphs::GetCustomGlyphList`メソッドを返します。 `E_NOTIMPL`、IDE によって提供されるグリフの既定の一覧からそのグリフを取得し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>