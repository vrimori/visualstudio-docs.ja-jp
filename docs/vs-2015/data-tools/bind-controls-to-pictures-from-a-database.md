---
title: データベースの画像にコントロールをバインド |Microsoft Docs
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
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fbaca836cb5b620c596b72bc991e91c1cfc2312c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189502"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>データベースの画像にコントロールをバインドする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
使用することができます、**データソース**データベース内のイメージをアプリケーションでのコントロールにバインドするウィンドウ。 イメージをバインドするなど、 <xref:System.Windows.Controls.Image> WPF アプリケーション、またはに制御を<xref:System.Windows.Forms.PictureBox>Windows フォーム アプリケーションで制御します。  
  
 データベースの画像は、通常はバイト配列として格納されます。 項目を**データ ソース**があるそのコントロール型のバイト配列として格納されているウィンドウを設定**None**既定では、バイト配列には、実行可能ファイルへのバイトの単純な配列から何も含めることができますので、大規模なアプリケーションです。 バイト配列項目のデータ バインド コントロールを作成する、**データソース**ウィンドウ イメージを表しますが、作成するコントロールを選択する必要があります。  
  
 次の手順を前提としていますが、**データ ソース**ウィンドウは、イメージにバインドされている項目が既に設定されています。 詳細については、「 [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md)」を参照してください。  
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>データベースの画像をコントロールにバインドするには  
  
1.  コントロールを追加するデザイン サーフェイスが WPF デザイナーまたは Windows フォーム デザイナーで開いていることを確認します。  
  
2.  **データソース**ウィンドウ、またはその列またはプロパティを表示するオブジェクトを目的のテーブルを展開します。  
  
3.  イメージ データを含む列またはプロパティを選択し、ドロップダウン コントロール リストから次のいずれかのコントロールを選択します。  
  
    -   WPF デザイナーが開いている場合は、選択**イメージ**します。  
  
    -   Windows フォーム デザイナーが開いている場合は、選択**PictureBox**します。  
  
    -   または、データ バインディングをサポートし、かつイメージを表示できる、別のコントロールを選択することもできます。 使用するコントロールが利用可能なコントロールの一覧にない場合は、一覧に追加し、それを選択します。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)

