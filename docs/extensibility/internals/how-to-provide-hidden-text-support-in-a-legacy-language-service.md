---
title: "方法: レガシ言語サービスで非表示のテキストをサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキストを非表示をサポートします。"
  - "エディター [Visual Studio SDK] が非表示テキスト"
  - "非表示のテキスト領域を実装する言語サービス"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: レガシ言語サービスで非表示のテキストをサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アウトライン領域のほか非表示のテキスト領域を作成できます。  非表示のテキスト領域はクライアント コントロールまたはコントロール エディターでテキストの領域を完全に非表示にするために使用されます。  エディターは横線が非表示の領域が表示されます。  次の例はスクリプトの HTML エディターのビューのみです。  
  
## 手順  
  
#### 非表示のテキストの領域を実行するには  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> の呼び出し `QueryService`。  
  
     これは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> へのポインターを返します。  
  
2.  指定したテキスト バッファーのポインターを渡す <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> を呼び出します。  これは非表示のテキストのセッションがバッファーに対して既に存在しているかどうかを判定します。  
  
3.  1 は既に存在する場合は1 を作成する必要はなく<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> の既存オブジェクトへのポインターを返します。  非表示のテキストの領域を列挙し作成するにはこのポインターを使用します。  それ以外の場合はバッファーの隠し文字のセッションを作成するの呼び出しの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> のオブジェクトへのポインターを返します。  
  
    > [!NOTE]
    >  `CreateHiddenTextSession` を呼び出すと隠し文字のクライアント \(つまり<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\) を指定できます。  隠し文字のクライアントは非表示のテキストまたはアウトラインがユーザーによって展開した状態または折りたたんだときに通知します。  
  
4.  一つ以上の新しいアウトライン領域を一度に追加するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> を呼び出して次の情報を `reHidReg` \(\)<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> のパラメーターに指定します :  
  
    1.  非表示の領域を作成するアウトライン領域ではなくことを示すために <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> の構造体の `iType` のメンバーで `hrtConcealed` の値を指定します。  
  
        > [!NOTE]
        >  表示するかどうかを示すために隠す場合は領域非表示になっている領域の周囲のエディターに表示された行自動的に非表示になります。  
  
    2.  領域が <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> の構造体のメンバー `dwBehavior` のエディターでクライアント コントロールまたはコントロールであるかどうかを指定します。  スマート アウトライン実装ではエディターおよびクライアント コントロールのアウトラインと非表示のテキスト領域の混在を含めることができます。