---
title: "プロジェクト階層ノード (C++) の名前の変更 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HierUtil7 サンプル [Visual Studio SDK]、プロジェクト ノードの名前の変更"
  - "プロジェクト ノード、HierUtil7 サンプルの名前の変更"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# プロジェクト階層ノード (C++) の名前の変更
アンマネージ C\+\+ に HierUtil7 プロジェクトのフレームワークを使用することでプロジェクトのフォルダー階層構造でノードの名前を変更できます。  詳細については、「[HierUtil7 Sample](http://msdn.microsoft.com/ja-jp/29c15184-a70c-4813-86c2-fb1d47442d11)」を参照してください。  
  
## 階層のノードの展開  
  
#### 階層のノードを展開しフォルダーの名前を変更するには  
  
1.  次のメソッドを使用して階層のノードを選択します。:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` はフォルダーに対応するコンテナーの階層で`EXPF_SelectItem` は <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> の列挙体です。  `GUID_MacroExplorer` は Vsshell.idl で定義されている GUID の定数でHu\_node.h で定義されている `ExtExpand` の関数のシグネチャの `rguidPersistenceSlot` の例です。  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     フォルダーは \\ Program Files \\ 8.0 \\ EnvSDK \<installation root\> VSIP \\ Common \\ hierutil7 の Hu\_node.h ファイルを検索できます :  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A> を使用して名前の変更コマンドを投稿してフォルダーの名前を変更します。  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` は <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> のポインターです : `<IVsUIShell>``srpVsUIShell`。  `guiVSStd97` は Vsshlids.h に定義されているコマンド `cmdidRename` が属するコマンド グループの一意の ID です。  
  
## 参照  
 [プロジェクトの種類を作成します。](../extensibility/internals/creating-project-types.md)   
 [VSSDK のサンプル](../misc/vssdk-samples.md)