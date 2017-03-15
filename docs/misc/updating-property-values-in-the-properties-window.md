---
title: "[プロパティ] ウィンドウでプロパティ値を更新 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[プロパティ] ウィンドウ、プロパティ値の更新"
  - "プロパティ値、[プロパティ] ウィンドウで更新"
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# [プロパティ] ウィンドウでプロパティ値を更新
**\[プロパティ\]** ウィンドウをプロパティ値の変更と同期するには、2 つの方法があります。 1 番目の方法は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイスを呼び出すことです。このインターフェイスは、環境によって用意されているツール ウィンドウやドキュメント ウィンドウのアクセスや作成を含む、基本的なウィンドウ操作機能へのアクセスを提供します。 次の手順は、この同期プロセスを説明したものです。  
  
## IVsUIShell を使ってプロパティ値を更新する  
  
#### IVsUIShell インターフェイスを使ってプロパティ値を更新するには  
  
1.  VSPackage、プロジェクト、エディターがツール ウィンドウまたはドキュメント ウィンドウを作成したり列挙したりする必要が生じた時点で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> を \(<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> サービスを通じて\) 呼び出します。  
  
2.  **\[プロパティ\]** ウィンドウと、プロジェクト \(または **\[プロパティ\]** ウィンドウで参照される、選ばれた他の任意のオブジェクト\) のプロパティの変更を同期するために、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> を実装します。これにより、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> の実装と <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> イベントの起動が必要なくなります。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> のメソッド <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> および <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> を実装します。この 2 つのメソッドは、それぞれ、階層イベントのクライアント通知を設定および無効化します。これにより、階層で <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> を実装する必要がなくなります。  
  
## IConnection を使ってプロパティ値を更新する  
 **\[プロパティ\]** ウィンドウとプロパティ値の変更を同期する 2 番目の方法は、接続可能なオブジェクトに `IConnection` を実装することにより、発信インターフェイスの存在を示すことです。 プロパティ名をローカライズする場合は、オブジェクトを <xref:System.ComponentModel.ICustomTypeDescriptor> から派生させます。<xref:System.ComponentModel.ICustomTypeDescriptor> の実装では、実装から返すプロパティ記述子を変更し、プロパティの名前を変更できます。 説明をローカライズするには、<xref:System.ComponentModel.DescriptionAttribute> から派生させた属性を作成し、Description プロパティをオーバーライドします。  
  
#### IConnection インターフェイスを実装する際の考慮事項  
  
1.  `IConnection` は、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを持つ列挙子サブオブジェクトへのアクセスを提供します。 また、すべての接続ポイント サブオブジェクトへのアクセスも提供し、それぞれは <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを実装します。  
  
2.  すべての参照オブジェクトは、<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> イベントを実装する必要があります。**\[プロパティ\]** ウィンドウは、`IConnection` を通してイベントを設定することをお勧めします。  
  
3.  接続ポイントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> の実装で許容される接続数 \(1 つまたは複数\) を制御します。 インターフェイスを 1 つのみ許容する接続ポイントでは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> メソッドから <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> を返すことができます。  
  
4.  クライアントは、`IConnection` インターフェイスを呼び出すことにより、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを持つ列挙子サブオブジェクトへのアクセスを取得できます。 その後、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> インターフェイスを呼び出すと、各発信インターフェイス ID \(IID\) の接続ポイントを列挙することができます。  
  
5.  また、`IConnection` を呼び出すことにより、各発信 IID への <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを持つ接続ポイント サブオブジェクトへのアクセスを取得することもできます。 クライアントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを通して、接続可能オブジェクトとクライアント自身の同期のアドバイザリ ループを開始または終了します。 クライアントは、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> インターフェイスを呼び出すこともできます。これにより、<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> インターフェイスを持つ列挙子オブジェクトを取得して、既知の接続を列挙します。  
  
## 参照  
 [プロパティ ウィンドウの選択の追跡の発表](/visual-cpp/misc/announcing-property-window-selection-tracking)   
 [プロパティを拡張します。](../extensibility/internals/extending-properties.md)