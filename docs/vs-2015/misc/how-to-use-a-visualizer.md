---
title: '方法: ビジュアライザーを使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: susanno
manager: douge
ms.openlocfilehash: cc158e0d84db56bc26262d60acd0fb8e92e47188
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544453"
---
# <a name="how-to-use-a-visualizer"></a>方法 : ビジュアライザーを使用する
ビジュアライザーを使用して、変数またはオブジェクトの内容を、データ型にとって意味のある方法で表示できます。 ビジュアライザーを使用することができます**データヒント**、**ウォッチ**ウィンドウで、 **[自動変数]** ウィンドウで、または**ローカル**ウィンドウ。  
  
 ビジュアライザーは、.NET Compact Framework ではサポートされていません。  
  
> [!NOTE]
>  **ストア**アプリ、標準のテキストのみ HTML、XML、および JSON ビジュアライザーがサポートされています。 カスタム (ユーザーが作成した) ビジュアライザーはサポートされていません。  
  
### <a name="to-open-a-visualizer"></a>ビジュアライザーを開くには  
  
1.  変数名の横に表示される、虫眼鏡アイコンをクリックします**データヒント**、**ウォッチ**ウィンドウ、または、 **[自動変数]**、**ローカル**、または。**クイック ウォッチ**ウィンドウ。  
  
     ビジュアライザーの一覧が表示されます。  
  
2.  使用するビジュアライザーをクリックします。  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>リモート デバッグ中にマネージド コードにビジュアライザーを使用するには  
  
-   デバッグ セッションを開始する前に、ビジュアライザー DLL をリモート コンピューターにコピーします。  
  
     DLL のパスは、リモート コンピューターとローカル コンピューター上で同じにする必要があります。 このパスは、次のいずれかの場所になります。  
  
     *Visual Studio のインストール パス* `\Common7\Packages\Debugger\Visualizers`  
  
     - または -  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio のバージョン* `\Visualizers`  
  
## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)   
 [方法: ビジュアライザーを記述します。](../debugger/how-to-write-a-visualizer.md)   
 [データ ヒントでのデータ値の表示](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)