---
title: "データベースからの画像をコントロールにバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77d2780200fd8be7a42d396cdade39b271b04bae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bind-controls-to-pictures-from-a-database"></a>データベースの画像にコントロールをバインドします。
使用することができます、**データソース**データベース内のイメージをアプリケーション内のコントロールにバインドするウィンドウです。 イメージをバインドするなど、<xref:System.Windows.Controls.Image>コントロール、WPF アプリケーションでまたは、 <xref:System.Windows.Forms.PictureBox> Windows フォーム アプリケーションで制御します。  
  
データベースの画像は、通常はバイト配列として格納されます。 項目を**データ ソース**バイトの配列であるコントロール型として格納されているウィンドウを設定**None**既定では、バイト配列には、実行可能ファイルにバイトの単純な配列から何も含めることができますので大規模なアプリケーションです。 バイト配列内の項目のデータ バインド コントロールを作成する、**データソース**を表すイメージ ウィンドウを作成するコントロールを選択する必要があります。  
  
次の手順の前提条件を**データソース**ウィンドウは、イメージにバインドされている項目に既に設定されています。 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>データベースの画像をコントロールにバインドするには  
  
1.  コントロールを追加するデザイン サーフェイスが WPF デザイナーまたは Windows フォーム デザイナーで開いていることを確認します。  
  
2.  **データソース** ウィンドウで、目的のテーブルを展開またはオブジェクトをその列またはプロパティを表示します。  
  
3.  イメージ データを含む列またはプロパティを選択し、ドロップダウン コントロール リストから次のいずれかのコントロールを選択します。  
  
    -   WPF デザイナーが開いている場合、**イメージ**です。  
  
    -   Windows フォーム デザイナーが開いている場合、 **PictureBox**です。  
  
    -   または、データ バインディングをサポートし、かつイメージを表示できる、別のコントロールを選択することもできます。 使用する場合、コントロールが利用できるコントロールの一覧にない場合は、一覧に追加でき、それを選択できます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。  
  
## <a name="see-also"></a>関連項目
[Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)