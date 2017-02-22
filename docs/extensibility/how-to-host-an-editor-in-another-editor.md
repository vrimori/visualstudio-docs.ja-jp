---
title: "方法: 別のエディターで、エディターのホスト | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - レガシ ホスト入れ子になったエディターは、"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 別のエディターで、エディターのホスト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio の親ウィンドウとしてホストするウィンドウを指定して1 種類のエディターの内部を別のホストできます。  そのためには子ウィンドウ フレームのパラメーター <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> と <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> を設定します。  
  
### ウィンドウ フレームをエディターをホストするように設定するには  
  
1.  子ウィンドウのウィンドウを作成するとホストのエディターとしてエディターを指定します。  
  
     このウィンドウはエディター内のテキストがその場所になります。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> のメソッドを使用してホストのエディターを作成します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> のメソッドにパラメーターとしてこれらのプロパティを渡すことによってホストされるエディターのウィンドウ フレームの実装の <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> と <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> のプロパティをそれぞれとに設定します。  
  
     これらのパラメーターを取得する必要がある場合 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> のメソッドにこれらのプロパティを渡します。  
  
4.  含まれているエディターの <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> のメソッドを呼び出します。  
  
     エディターが含まれているエディターのホスト ウィンドウに表示されます。  
  
## 信頼性の高いプログラミング  
 別のエディターをホストするアーキテクトの Visual Studio Team Edition の **\*\*\* Application Designer \*\*\***エディター ウィンドウ フレームの例です。  **\*\*\* Application Designer \*\*\***右側のペインの他のデザイナーをホストします。  含まれているデザイナーのデザイナーのパネル \(または \[\]\) のページ ENT0ENT 含むウィンドウ枠に追加されます。