---
title: "方法: シンボル ライブラリ内の特定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "呼び出しブラウザー ツール、ライブラリ内のシンボルを識別します。"
  - "呼び出しブラウザー ツール"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: シンボル ライブラリ内の特定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルのツールの階層構造のシンボル参照。  シンボルはオブジェクト名前空間クラスクラス メンバーおよびそのほかの言語要素を表します。  
  
 階層の各シンボルは次のインターフェイスを通じて [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト ライブラリ マネージャーにシンボルをナビゲーション情報によって識別できます :  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 階層のシンボルの場所からシンボルを区別します。  これは特定のシンボルに移動するためのツールをシンボル参照しています。  一意のシンボルへの絶対パス位置を決定します。  パス内の各要素はノードです。  最上位ノードとのパスが開始され特定のシンボルを使用して終了します。  たとえばたとえばメソッドが C1 クラスのメンバーでありC1 が N1 名前空間にあるたとえばメソッドの完全パスは N1.C1.M1 です。  このパスは3 種類のノードが含まれています : N1C1 と M1。  
  
 ナビゲーション情報は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーを選択するために検索できるようにしておくには階層のシンボルを選択します。  次の 1 とおりのブラウザー ツール間を移動できるようにします。  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] のシンボルを参照するために  **オブジェクト ブラウザー**  を使用するとプロジェクトメソッドを右クリックしメソッドの呼び出しでグラフを表示 ENT1ENT \[入力\] ツールを開始できます。  
  
 2 とおりの形式はシンボルの場所について説明します。  正規化形式はシンボルの完全修飾パスに基づいています。  これは階層内のシンボルの一意の位置を表します。  これはシンボル参照するツールに依存しません。  正規化形式情報を取得するには[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーは <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> のメソッドを呼び出します。  表示形式は特定のシンボル参照のツール内のシンボルの場所について説明します。  シンボルの場所は hierarchicy のそのほかの記号の位置を基準にしています。  特定のシンボルは二つ以上表示のパス1 種類の正規のパスのみがあります。  たとえばC1 C2 クラスがクラスを継承しクラスが両方とも N1 名前空間にある場合 **オブジェクト ブラウザー**  は次の階層ツリーが表示されます :  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 クラスの正規のパスはこの例ではN1 \+ C2 あります。  C2 表示のパスは 「 C1 とベースおよびインターフェイス」ノードが含まれています : N1 C1 \+ \+ 「 \+ 」 C2 ベースおよびインターフェイス。  
  
 表示形式の情報を取得するにはオブジェクト マネージャーは <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> のメソッドを呼び出します。  
  
## 階層内のシンボル ID  
  
#### 標準と表示形式の情報を取得します。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> メソッドを実装します。  
  
     オブジェクト マネージャーはシンボルの正規のパスに含まれるノードのリストを取得するときにこのメソッドを呼び出します。  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> メソッドを実装します。  
  
     オブジェクト マネージャーはシンボルのパスに含まれるノードのリストを取得するときにこのメソッドを呼び出します。  
  
## 参照  
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [方法: オブジェクト マネージャにライブラリを登録](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)