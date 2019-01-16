---
title: データの保存前にデータ バインド コントロールで実行中の編集をコミットする
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
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e4ab8d46bd9c19a747231f87eb7ef0bd40025c69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824406"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>データの保存前にデータ バインド コントロールで実行中の編集をコミットする

データ バインド コントロール内の値を編集するには、ユーザーを更新された値に、コントロールがバインドされている基になるデータ ソースにコミットする現在のレコードを移動する必要があります。 項目をドラッグすると、[データ ソース ウィンドウ](add-new-data-sources.md)を削除する最初の項目のフォームへにコードが生成されます、**保存**ボタン クリックしてイベントの<xref:System.Windows.Forms.BindingNavigator>します。 このコードは、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>します。 呼び出しでは、そのため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドは、最初にのみ生成<xref:System.Windows.Forms.BindingSource>フォームに追加されています。

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼び出しは、現在編集中のデータ バインド コントロールで実行されている変更をコミットします。 したがって、あるデータ バインド コントロールにフォーカスがある状態で **[保存]** ボタンをクリックすると、実際の保存 (`TableAdapterManager.UpdateAll` メソッド) が実行される前に、そのコントロール内のすべての保留中の編集がコミットされます。

自動的に変更をコミットするアプリケーションを構成するには、ユーザーが、保存の一部として変更をコミットせずにデータを保存しようとしています。 場合でもプロセス。

> [!NOTE]
> デザイナーに追加、`BindingSource.EndEdit`最初の項目に対してのみコードがフォームにドロップします。 呼び出すコード行を追加する必要があるため、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>形式にします。 呼び出すコード行を手動で追加することができます、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>します。 また、追加することができます、`EndEditOnAllBindingSources`をフォームにメソッドと保存を実行する前に付けます。

次のコードでは、 [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)すべてを反復処理するクエリ<xref:System.Windows.Forms.BindingSource>コンポーネントと呼び出し、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>メソッドごとに<xref:System.Windows.Forms.BindingSource>フォームで。

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>フォーム上のすべての BindingSource コンポーネントの EndEdit を呼び出す

1.  次のコードを含むフォームを追加、<xref:System.Windows.Forms.BindingSource>コンポーネント。

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  次のフォームのデータを保存する呼び出しのすぐ前に、のコード行を追加 (、`TableAdapterManager.UpdateAll()`メソッド)。

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [階層更新](../data-tools/hierarchical-update.md)