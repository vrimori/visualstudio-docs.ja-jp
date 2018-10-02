---
title: Visual Studio でのデータへの Windows フォーム コントロールのバインド |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce8945fd535f92a15d510a56e9bc39fd178317f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546386"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows フォーム コントロールを Visual Studio でのデータ バインドします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio でのデータにコントロールを Windows フォームのバインド](https://docs.microsoft.com/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)します。  
  
  
データを Windows フォームにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグすることができます、**データソース**Visual Studio での Windows フォーム デザイナー ウィンドウ。 このトピックでは、データ バインド Windows フォーム アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。  
  
 ![データ ソースはドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata データ ソースはドラッグ操作")  
  
 Visual Studio でのデータ バインド コントロールを作成する方法については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。 Windows フォームでのデータ バインディングの詳細については、次を参照してください。 [Windows フォーム データ バインディング](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [Windows フォーム コントロールをデータにバインドする](../data-tools/bind-windows-forms-controls-to-data.md)  
  
-   [データの保存前にデータ バインド コントロールで実行中の編集をコミットする](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
  
-   [Windows フォーム アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-windows-forms-applications.md)  
  
-   [データを検索する Windows フォームを作成する](../data-tools/create-a-windows-form-to-search-data.md)  
  
-   [単純なデータ バインディングをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
  
-   [複合データ バインディングをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
  
-   [ルックアップ データ バインディングをサポートする Windows フォーム ユーザー コントロールの作成](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
  
-   [フォーム間でデータを渡す](../data-tools/pass-data-between-forms.md)  
  
## <a name="bindingsource-component"></a>BindingSource コンポーネント  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは 2 つの目的で利用できます。 まず、フォームのコントロールをデータにバインドするときに、抽象化レイヤーの役割を果たします。 フォーム上のコントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントにバインドされます (データ ソースに直接バインドされるわけではありません)。  
  
 また、オブジェクトのコレクションを管理できます。 <xref:System.Windows.Forms.BindingSource> に型を追加すると、その型の一覧が作成されます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントの詳細については、次のトピックを参照してください。  
  
-   [BindingSource コンポーネント](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)  
  
-   [BindingSource コンポーネントの概要](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
-   [BindingSource コンポーネント アーキテクチャ](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)  
  
## <a name="bindingnavigator-control"></a>BindingNavigator コントロール  
 このコンポーネントには、Windows アプリケーションによって表示されるデータを移動するためのユーザー インターフェイスが用意されています。 詳細については、「[BindingNavigator コントロール](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)」を参照してください。  
  
## <a name="datagridview-control"></a>DataGridView コントロール  
 表示し、さまざまな種類のデータ ソースから表形式のデータを編集、使用、<xref:System.Windows.Forms.DataGridView>コントロール。 <xref:System.Windows.Forms.DataGridView> にデータをバインドするには、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを使用します。 詳細については、次を参照してください。 [DataGridView コントロールの概要](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)

