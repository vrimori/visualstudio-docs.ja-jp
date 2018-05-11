---
title: データを保存する前にデータ バインド コントロールでの中の編集をコミットします。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a0811ec9338bfb84235679a68d32169435eb57a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>データを保存する前にデータ バインド コントロールでの中の編集をコミットします。

データ バインド コントロール内の値を編集するには、ユーザーが更新された値に、コントロールがバインドされている、基になるデータ ソースにコミットする現在のレコードに移動する必要があります。 項目をドラッグすると、[データ ソース ウィンドウ](add-new-data-sources.md)、フォームに最初の項目を削除するにのコードを生成、**保存**ボタン クリックしてイベントの<xref:System.Windows.Forms.BindingNavigator>です。 このコードを呼び出す、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>です。 呼び出し、そのため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドは、最初にのみ生成<xref:System.Windows.Forms.BindingSource>ですが、フォームに追加します。

<xref:System.Windows.Forms.BindingSource.EndEdit%2A>呼び出しは、現在編集中のデータ バインド コントロールでは、プロセス内にある変更をコミットします。 そのため、データ バインド コントロールがあるフォーカス クリックして、**保存** ボタン、保留中のすべての編集コントロールは、実際の保存前にコミットされます。 その (、`TableAdapterManager.UpdateAll`メソッド)。

自動的に変更をコミットするアプリケーションを構成するには、ユーザーが、保存の一部として、変更をコミットすることがなくデータを保存しようとした場合でも処理できます。

> [!NOTE]
> デザイナーに追加、`BindingSource.EndEdit`最初の項目に対してのみコードをフォームにドロップします。 呼び出すコード行を追加する必要があるため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>ごとメソッド<xref:System.Windows.Forms.BindingSource>フォームにします。 呼び出すコード行を手動で追加することができます、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>ごとメソッド<xref:System.Windows.Forms.BindingSource>です。 また、追加することができます、`EndEditOnAllBindingSources`をフォームにメソッドおよび保存を実行する前に呼び出しです。

次のコードでは、[クエリ (LINQ: Language-Integrated)](/dotnet/csharp/linq/)すべてを反復処理するクエリ<xref:System.Windows.Forms.BindingSource>コンポーネントと呼び出し、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>ごとメソッド<xref:System.Windows.Forms.BindingSource>フォーム上。

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>For を呼び出す EndEdit フォーム上のすべての BindingSource コンポーネント

1.  次のコードを含むフォームを追加、<xref:System.Windows.Forms.BindingSource>コンポーネントです。

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  すぐに呼び出しの前に、フォームのデータを保存するコードの次の行を追加 (、`TableAdapterManager.UpdateAll()`メソッド)。

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [階層更新](../data-tools/hierarchical-update.md)