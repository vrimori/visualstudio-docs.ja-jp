---
title: データを保存する前にデータ バインド コントロールの中の編集をコミット |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3af1534e6436eec2eac1f294be8c2428c949ce9d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296036"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>データの保存前にデータ バインド コントロールで実行中の編集をコミットする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データ バインド コントロール内の値を編集するには、ユーザーを更新された値に、コントロールがバインドされている基になるデータ ソースにコミットする現在のレコードを移動する必要があります。 項目をドラッグすると、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)を削除する最初の項目のフォームへにコードが生成されます、**保存**ボタン クリックしてイベントの<xref:System.Windows.Forms.BindingNavigator>します。 このコードは、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>します。 呼び出しでは、そのため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドは、最初にのみ生成<xref:System.Windows.Forms.BindingSource>フォームに追加されています。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>呼び出しは、現在編集中のデータ バインド コントロールの処理の変更をコミットします。 そのため、データ バインド コントロールがまだ場合フォーカスをクリックして、**保存**ボタン、保留中のすべての編集コントロールは、実際の保存の前にコミットされたことで (、`TableAdapterManager.UpdateAll`メソッド)。  
  
 自動的に変更をコミットするアプリケーションを構成するには、ユーザーが、保存の一部として変更をコミットせずにデータを保存しようとしています。 場合でもプロセス。  
  
> [!NOTE]
>  デザイナーに追加、`BindingSource.EndEdit`最初の項目に対してのみコードがフォームにドロップします。 呼び出すコード行を追加する必要があるため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>形式にします。 呼び出すコード行を手動で追加することができます、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>します。 また、追加することができます、`EndEditOnAllBindingSources`をフォームにメソッドと保存を実行する前に付けます。  
  
 次のコードでは、 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)すべてを反復処理するクエリ<xref:System.Windows.Forms.BindingSource>コンポーネントと呼び出し、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>フォームで。  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>フォーム上のすべての BindingSource コンポーネントの EndEdit を呼び出す  
  
1.  次のコードを含むフォームを追加、<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  次のフォームのデータを保存する呼び出しのすぐ前に、のコード行を追加 (、`TableAdapterManager.UpdateAll()`メソッド)。  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [階層更新](../data-tools/hierarchical-update.md)

