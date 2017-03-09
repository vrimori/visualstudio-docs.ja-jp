---
title: "方法: タスク一覧のカスタム カテゴリを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "タスク一覧、カスタム カテゴリ"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 方法: タスク一覧のカスタム カテゴリを作成する
タスクのカスタム カテゴリはタスクが ENT5ENT \[入力\] ウィンドウでどのように表示するかを制御できます。  
  
 次に示す理由によりタスクのカスタム カテゴリを実行する :  
  
-   カテゴリはカテゴリの一覧の並べ替え \(\) の場所に表示するかを制御する場合。  
  
-   その中に使用するそのほかのタスクを持たない 1 種類に分類するタスクのサブカテゴリがあります。  
  
-   タスクだけを表示するカスタム ビューを作成する場合。  
  
    > [!NOTE]
    >  実際にカスタム カテゴリを実行せずにカスタム カテゴリと同様の効果を実現できます。  たとえば<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A> を実行してカテゴリのビットマップまたはサブカテゴリを表示できます。  タスクのプロバイダーはリストを指定し各タスクがリストのインデックスを指定します。  
  
 **タスク一覧**  のカスタム カテゴリを作成するには次の手順に従って  **タスク一覧**  に登録します。  
  
### カスタム タスクの一覧にあるカテゴリを登録するには  
  
-   タスク一覧でカスタム カテゴリを登録するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> を呼び出します。  
  
     各カスタム カテゴリは `guidCat` のパラメーターで指定される独自の GUID が必要です。  `dwSortOrder` のパラメーターではリストがカテゴリ別に並べ替えるとき\) に並べ替えます。このカテゴリを取得する場所を指定します。  このメソッドはカテゴリの大きいリスト内のカスタム カテゴリの実際の並べ替えの配置を返します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY> の列挙型で定義されている組み込みのタスク カテゴリの並べ替え順序を次の表に示します。  
  
    |\[カテゴリ\]|値|Description|  
    |--------------|-------|-----------------|  
    |CAT\_ALL|1|は実際のカテゴリ。  タスク一覧のビューが  **タスク一覧**  のすべてのタスクを示す使用します。|  
    |CAT\_BUILDCOMPILE|10|ビルド エラー警告およびエラーの配置。|  
    |CAT\_COMMENTS|20|TODO 「」元に返されて」または 「 HACK のような特殊なコメントによって生成されるタスク」。|  
    |CAT\_CODESENSE|30|は型として生成されるエラーのソース・コードです。|  
    |CAT\_SHORTCUTS|40|コードへのショートカットです。|  
    |CAT\_USER|50|ユーザーが入力するタスク。|  
    |CAT\_MISC|60|VSPackage が  **タスク一覧**  に追加する可能性があるそのほかのタスク。|  
    |CAT\_HTML|70|Web ページの開発に関連するタスク。|  
  
     たとえばCAT\_CODESENSE と CAT\_SHORTCUTS 間のカテゴリが含まれるように並べ替え順序での 31 という値を渡す場合があります。  ただし値が 31 である他のカスタム作業のカテゴリのプロバイダーによって既に使用されている可能性があるため  **タスク一覧**  は次のタスク カテゴリがスロットを作る割り当てます。  この値は `pCat` のパラメーターで返されます。  
  
### カスタム タスクの一覧にあるカテゴリの登録を解除します。  
  
-   カスタム カテゴリの登録を解除するの呼び出しの <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A>。  
  
## 参照  
 [カスタム タスク リスト ビューの作成](/visual-cpp/misc/creating-custom-task-list-views)