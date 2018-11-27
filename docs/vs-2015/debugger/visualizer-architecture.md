---
title: ビジュアライザーのアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7a3255b8e8b91f074308a0238719f26af6cf665
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736165"
---
# <a name="visualizer-architecture"></a>ビジュアライザーのアーキテクチャ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

デバッガー ビジュアライザーのアーキテクチャには、次の 2 つの部分があります。  
  
- *デバッガー側*Visual Studio デバッガー内で実行します。 デバッガー側のコードは、ビジュアライザーのユーザー インターフェイスを作成し、表示します。  
  
- *デバッグ対象側*Visual Studio がデバッグ プロセス内で実行 (、*デバッグ対象*)。  
  
  ビジュアライザーは、デバッガーを表示できるようにするデバッガー コンポーネント (*視覚化*)、意味のある理解しやすい形式でデータ オブジェクトの内容。 データ オブジェクトの編集をサポートするビジュアライザーもあります。 カスタム ビジュアライザーを作成すれば、独自のデータ型を処理できるようにデバッガーを拡張することも可能です。  
  
  デバッグ中のプロセス内にあります。 視覚化対象であるデータ オブジェクト (、*デバッグ対象*プロセス)。 データを表示するユーザー インターフェイスは、Visual Studio デバッガー プロセス内で作成されます。  
  
|デバッガー プロセス|デバッグ対象プロセス|  
|----------------------|----------------------|  
|デバッガーのユーザー インターフェイス (データヒント、ウォッチ ウィンドウ、クイック ウォッチ)|視覚化の対象となるデータ オブジェクト|  
  
 デバッガーのインターフェイス内でデータ オブジェクトを視覚化するには、2 つのプロセス間の通信を実現するためのコードを記述する必要があります。 そのため、ビジュアライザーのアーキテクチャを 2 つの部分で構成されます:*デバッガー側*コードと*デバッグ対象側*コード。  
  
 デバッガー側コードでは、自身のユーザー インターフェイスが作成されます。このインターフェイスは、デバッガーのインターフェイス (データヒント、ウォッチ ウィンドウ、またはクイック ウォッチ) から呼び出すことができます。 ビジュアライザーのインターフェイスは、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> クラスおよび <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> インターフェイスを使用して作成します。 ビジュアライザーのすべての API に共通することですが、DialogDebuggerVisualizer および IDialogVisualizerService は、<xref:Microsoft.VisualStudio.DebuggerVisualizers> 名前空間に存在します。  
  
|デバッガー側|デバッグ対象側|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer クラス<br /><br /> IDialogVisualizerService インターフェイス|データ オブジェクト|  
  
 ユーザー インターフェイスは、視覚化の対象となるデータを、デバッガー側に存在するオブジェクト プロバイダーから取得します。  
  
|デバッガー側|デバッグ対象側|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer クラス<br /><br /> IDialogVisualizerService インターフェイス|データ オブジェクト|  
|オブジェクト プロバイダー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> を実装)||  
  
 デバッグ対象側には、対応するオブジェクトが存在します。これをオブジェクト ソースと呼びます。  
  
|デバッガー側|デバッグ対象側|  
|-------------------|-------------------|  
|DialogDebuggerVisualizer クラス<br /><br /> IDialogVisualizerService インターフェイス|データ オブジェクト|  
|オブジェクト プロバイダー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> を実装)|オブジェクト ソース (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> から派生)|  
  
 オブジェクト プロバイダーは、視覚化の対象となるオブジェクト データをビジュアライザーの UI に提供します。 オブジェクト プロバイダーは、このオブジェクト データをオブジェクト ソースから取得します。 オブジェクト プロバイダーおよびオブジェクト ソースには、デバッガー側とデバッグ対象側との間でオブジェクト データをやり取りするための API が用意されています。  
  
 ビジュアライザーはすべて、視覚化の対象となるデータ オブジェクトを取得する必要があります。 次の表は、この目的で使用されるオブジェクト プロバイダーの API と、それに対応するオブジェクト ソースの API を示しています。  
  
|オブジェクト プロバイダー|オブジェクト ソース|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> または<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 オブジェクト プロバイダーには、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> と <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> の 2 つの API が存在しています。 どちらの API を使用しても、オブジェクト ソースの <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> が呼び出されます。 呼び出し<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName>[System.IO.Stream] を入力 (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->)、視覚化対象であるオブジェクトのシリアル化された形式を表します。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> では、データがオブジェクト形式へと逆シリアル化されるため、このデータをそのまま <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> で作成した UI に表示できます。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> では、データが未加工の <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> として格納されるため、これは別途、逆シリアル化する必要があります。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> は、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> を呼び出してシリアル化された <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> を受け取り、そのデータを逆シリアル化するという処理を行います。 オブジェクトを .NET でシリアル化できないなど、カスタムのシリアル化が必要な場合は、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> を使用してください。 そのような場合は、<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> メソッドをオーバーライドする必要があります。  
  
 読み取り専用のビジュアライザーを作成する場合は、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> または <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> を使った一方向の通信で十分です。 データ オブジェクトの編集をサポートするビジュアライザーを作成する場合、それだけでは不十分です。 オブジェクト プロバイダーからオブジェクト ソースへと、データ オブジェクトを戻す機能が必要となります。 次の表は、この目的で使用される、オブジェクト プロバイダーとオブジェクト ソースの API を示しています。  
  
|オブジェクト プロバイダー|オブジェクト ソース|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> または<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 ここでも、オブジェクト プロバイダーには、使用できる API が 2 つ存在します。 データは常に <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> としてオブジェクト プロバイダーからオブジェクト ソースへと送られますが、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> の場合は、別途、オブジェクトを <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> にシリアル化する処理が必要となります。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> は、指定したオブジェクトを受け取り、それを <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> にシリアル化した後、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> を呼び出して、<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> を <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> に送ります。  
  
 いずれかの Replace メソッドを使用すると、視覚化対象であるオブジェクトを置き換える新しいデータ オブジェクトがデバッグ対象側に作成されます。 オブジェクトそのものを置き換えずに、元のオブジェクトの内容を変更する場合は、次の表に示した、いずれかの Transfer メソッドを使用してください。 これらの API では、視覚化対象であるオブジェクトを置き換えることなく、データが双方向で同時に転送されます。  
  
|オブジェクト プロバイダー|オブジェクト ソース|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> または<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>関連項目  
 [方法: ビジュアライザーを記述します。](../debugger/how-to-write-a-visualizer.md)   
 [チュートリアル: c# でビジュアライザーを記述します。](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [チュートリアル: Visual Basic でビジュアライザーを記述します。](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [チュートリアル: Visual Basic でビジュアライザーを記述します。](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [ビジュアライザーのセキュリティに関する考慮事項](../debugger/visualizer-security-considerations.md)



