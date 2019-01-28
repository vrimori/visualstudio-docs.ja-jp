---
title: '方法: オブジェクトからのデータをドキュメントに読み込む'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 571c010aa8b9cda1002a152ed2d528e22b1aa57e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865789"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>方法: オブジェクトからのデータをドキュメントに読み込む

Microsoft Office Word のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータ オブジェクトのデータにアクセスできます。 同じツールとコードを使用してオブジェクトからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 また、ホスト コントロールを使用してデータを表示することもできます。 ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

ドキュメントにオブジェクトのデータを読み込むには、次の 3 つの基本手順を実行する必要があります。

-   データにバインドできるドキュメントにコントロールを追加する。

-   データ オブジェクトをドキュメントに追加する。

-   データ オブジェクトを BindingSource に接続する。

## <a name="to-add-a-data-object"></a>データ オブジェクトを追加するには

データ オブジェクトを追加するには、開く、**データ ソース**ウィンドウ オブジェクトからデータ ソースを作成します。 詳細については、「[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)」を参照してください。

## <a name="connect-the-data-object-to-the-bindingsource"></a>データ オブジェクトを BindingSource に接続します。

ドキュメント レベルのプロジェクトでは、デザイン時にコントロールを文書に追加し、そのコントロールをデータにバインドできます。

VSTO アドイン プロジェクトでは、コントロールを作成して、そのコントロールを実行時にバインドできます。

### <a name="document-level-projects"></a>ドキュメント レベルのプロジェクト

データ オブジェクトを BindingSource に接続します。

1.  **[データ ソース]** ウィンドウから目的のデータ フィールドを文書にドラッグします これにより、コントロールが自動的に作成されます。

2.  コードで、データ ソースとして選択したオブジェクトの種類のインスタンスを作成します。

3.  このインスタンスを <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource>プロパティに割り当てます。

### <a name="application-level-projects"></a>アプリケーション レベルのプロジェクト

データ オブジェクトを BindingSource に接続します。

1.  コード中に、データ ソースに関連付けられているオブジェクトの種類のインスタンスを作成します。

2.  <xref:System.Windows.Forms.BindingSource>のインスタンスを作成します。

3.  データ ソースのインスタンスを <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource>プロパティに割り当てます。

4.  コントロールへのデータ バインディングとしてデータ ソースを追加します。

## <a name="see-also"></a>関連項目

- [新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)
- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [方法: ホスト コントロールからのデータでデータ ソースを更新します。](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)