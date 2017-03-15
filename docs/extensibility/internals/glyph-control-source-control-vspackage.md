---
title: "グリフ コントロール (ソース コントロールの vs パッケージ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理パッケージのグリフ"
  - "グリフのソース管理パッケージ"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# グリフ コントロール (ソース コントロールの vs パッケージ)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理 VSPackage と緊密に統合の部分はソース管理された項目の状態を示すための独自のグリフを表示する機能です。  
  
## グリフのコントロールのレベル  
 状態のグリフはたとえば  **ソリューション エクスプローラー**  または  **クラス ビュー**  で表示される項目の現在の状態を示すアイコンです。  ソース管理 VSPackageグリフのコントロールの 2 レベルを実行できます。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE によって提供されるグリフの定義済みセットにグリフが選択できるようにしたり表示するグリフのカスタム設定を定義できます。  
  
### グリフの既定の設定  
 **ソリューション エクスプローラー**  の項目に関連付けられた状態のグリフをプロジェクトのソース管理から要求の状態のグリフ <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> を使用して確認する。  ソース管理 VSPackage はIDE で定義済みのグリフに制限されるグリフを選択する場合もあります。  この場合VSPackage は vsshell.idl で定義されるグリフ列挙型を表す値の配列を渡します。  詳細については<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> を参照してください。これは 「チェックインされた」グリフの錠などの IDEおよびの各チェック マーク 「グリフをチェックするようにグリフの定義済みセット設定します。  
  
### グリフのカスタム設定  
 インストール時にソース管理 VSPackage は一意の外観 「」に対して独自のグリフを使用できます。  新しいソース管理 VSPackage はアクティブな場合前のソース管理 VSPackage がまだ読み込まれてアクティブが独自のグリフを使用して呼び出すことが必要です。  このモードでは選択したソース管理はVSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に一貫した外観を維持するために既存のアイコンを使用できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> サービスがサポートするインターフェイスVSPackage がIDE での実装で<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>。  IDE が要求を行う場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は現在登録されたソース管理から VSPackage このインターフェイスを取得することを試みます。  インターフェイスを登録した場合VSPackage にカスタムグリフの IDE の確認要求は成功します ; それ以外 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE でグリフの既定の設定を使用します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> のメソッドはさまざまなソース管理の状態を示すイメージの一覧を取得するために使用します。  VSPackage はソース管理カスタムグリフのイメージ リストに IDE のハンドルを返します。  IDE ではイメージ リストを表示するためにコピーを作成しこの時点でグリフを選択するために後で使用します。  新しいインターフェイスが `IVsSccGlyphs::GetCustomGlyphList` のメソッドから E\_NOTIMPL をサポートする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって提供されるグリフの既定の一覧からグリフを取得します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>