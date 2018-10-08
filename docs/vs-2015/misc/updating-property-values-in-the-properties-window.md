---
title: '[プロパティ] ウィンドウでプロパティ値を更新する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537778"
---
# <a name="updating-property-values-in-the-properties-window"></a>[プロパティ] ウィンドウでプロパティ値を更新
**[プロパティ]** ウィンドウをプロパティ値の変更と同期するには、2 つの方法があります。 最初に呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>へのアクセスと、環境によって提供されるツールとドキュメント ウィンドウの作成など、基本的なウィンドウ操作機能へのアクセスを提供するインターフェイス。 次の手順は、この同期プロセスを説明したものです。  
  
## <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell を使ってプロパティ値を更新する  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell インターフェイスを使ってプロパティ値を更新するには  
  
1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(を通じて<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>サービス) いつでも、Vspackage、プロジェクト、またはエディターを作成したり、ツールまたはドキュメント ウィンドウを列挙したりする必要があります。  
  
2.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持する、**プロパティ**ウィンドウとプロジェクトのプロパティの変更を同期 (またはによって参照されているその他の選択したオブジェクト、**プロパティ**ウィンドウ)を実装することがなく<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>および発生<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>イベント。  
  
3.  実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>を確立し、それぞれ実装するために、階層を必要とせず、階層イベントのクライアント通知を無効にする<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。  
  
## <a name="updating-property-values-using-iconnection"></a>IConnection を使ってプロパティ値を更新する  
 **[プロパティ]** ウィンドウとプロパティ値の変更を同期する 2 番目の方法は、接続可能なオブジェクトに `IConnection` を実装することにより、発信インターフェイスの存在を示すことです。 プロパティ名をローカライズする場合は、派生オブジェクトの<xref:System.ComponentModel.ICustomTypeDescriptor>します。 <xref:System.ComponentModel.ICustomTypeDescriptor>実装が返すプロパティ記述子を変更して、プロパティの名前を変更します。 説明をローカライズするから派生する属性を作成します。<xref:System.ComponentModel.DescriptionAttribute>と説明のプロパティをオーバーライドします。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection インターフェイスを実装する際の考慮事項  
  
1.  `IConnection` 列挙子サブオブジェクトへのアクセスを提供します、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイス。 すべての接続ポイント サブオブジェクトへのアクセスも用意されています。 それぞれの実装、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイス。  
  
2.  すべての参照オブジェクトを実装する責任を負いますが、<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>イベント。 **[プロパティ]** ウィンドウは、 `IConnection`を通してイベントを設定することをお勧めします。  
  
3.  接続ポイントの実装でできます (1 つまたは複数) の接続の数を制御する<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>します。 1 つだけのインターフェイスをできるようにする接続ポイントを返すことができます<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>から、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>メソッド。  
  
4.  クライアントが呼び出すことができます、`IConnection`で列挙子サブオブジェクトへのアクセスを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイス。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>インターフェイスは、各発信インターフェイス ID (IID) の接続ポイントを列挙し、呼び出すことができます。  
  
5.  `IConnection` 接続でのポイント サブオブジェクトへのアクセスの取得を呼び出すこともできます、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>各発信 IID のインターフェイス。 を通じて、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>インターフェイス、クライアントが開始または接続可能オブジェクトとクライアントの同期のアドバイザリ ループを終了します。クライアントが呼び出すことも、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>を持つ列挙子オブジェクトを取得するインターフェイス、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>について認識して接続を列挙するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ ウィンドウの選択の追跡の発表](../misc/announcing-property-window-selection-tracking.md)   
 [プロパティの拡張](../extensibility/internals/extending-properties.md)