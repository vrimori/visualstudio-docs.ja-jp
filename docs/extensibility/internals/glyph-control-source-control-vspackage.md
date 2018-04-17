---
title: グリフ コントロール (ソース コントロール VSPackage) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: c3787b0afad7f89743950a922d5b19c2d204bdd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="glyph-control-source-control-vspackage"></a>グリフ コントロール (ソース コントロール VSPackage)
ソース管理の Vspackage を使用できる高度な統合の一部は、ソース管理下にある項目の状態を示すために、独自のグリフを表示する機能です。  
  
## <a name="levels-of-glyph-control"></a>レベルのグリフの制御  
 状態のグリフが表示される場合の例の場合、項目の現在の状態を示すアイコン**ソリューション エクスプ ローラー**または**クラス ビュー**です。 ソース管理 VSPackage 2 レベルのグリフのコントロールの操作を行えます。 によって提供されるグリフの定義済みセットへのグリフの選択を制限することができます、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE、またはそれが表示されるグリフのカスタム セットを定義できます。  
  
### <a name="default-set-of-glyphs"></a>グリフの既定のセット  
 内の項目に関連付けられている状態のグリフを決定する**ソリューション エクスプ ローラー**、プロジェクトを使用してソース コントロールからの状態のグリフの要求、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>です。 ソース管理 VSPackage は、IDE によって提供される定義済みのグリフに制限されたグリフの選択を保持することができます。 ここでは、VSPackage vsshell.idl で定義されているグリフ列挙型を表す値の配列を渡します戻します。 詳細については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>です。これは、定義済みの設定では、「チェックイン」グリフと「チェック アウト」グリフとしてチェック マークの南京錠などの IDE からのグリフのセットです。  
  
### <a name="custom-set-of-glyphs"></a>グリフのカスタム セット  
 インストールされている場合、ソース管理 VSPackage は、一意な「ルック アンド フィール」を独自のグリフを使用できます。 新しいソース管理 VSPackage がアクティブである場合、独自のグリフ場合でも、以前のソース制御 VSPackage がまだ読み込まれて使用を開始することが、非アクティブになります。 このモードでソース管理 VSPackage まだ既存するアイコンを使用、外観と一貫性を維持するために[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]選択した場合。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>サービスが、インターフェイスをサポートしている<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>これ、VSPackage をオプションで実装され、これが要求されます、IDE によってです。 IDE は、要求を行うときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 現在登録されているソース管理からこのインターフェイスを取得する順番を試みます。 登録済みの VSPackage でインターフェイスが存在する場合にカスタム グリフの IDE の要求が成功しました。それ以外の場合、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は一連の既定のグリフを使用します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>メソッドによって使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の状態を示すさまざまなソース管理のイメージの一覧を取得します。 ソース管理 VSPackage は、IDE にそのカスタム グリフのイメージ リストへのハンドルを返します。 IDE では、この時点でイメージ リストのコピーを作成し、それを表示するグリフの選択を後で使用します。 新しいインターフェイスがサポートされていない場合、または`IVsSccGlyphs::GetCustomGlyphList`メソッドは、IDE によって提供されるグリフの既定の一覧からそのグリフを取得し、E_NOTIMPL を返します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>