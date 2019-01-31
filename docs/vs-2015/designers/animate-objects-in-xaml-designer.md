---
title: XAML デザイナーでのオブジェクトのアニメーション化 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7846ade8dba2ce849acf62311e508c157b07dd3e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54805510"
---
# <a name="animate-objects-in-xaml-designer"></a>XAML デザイナーでのオブジェクトのアニメーション化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

オブジェクトを動かす短いアニメーションを作成したり、フェードインとフェードアウトを行うことができます。  
  
 最初に、 *ストーリー ボード*を作成します。 ストーリー ボードには、1 つ以上の *タイムライン*があります。 タイムライン上で *キーフレーム* を設定してプロパティの変更をマークします。 次に、アニメーションの実行時に、Blend は、指定した期間全体でプロパティの変更を補間します。 結果として、移行がスムーズになります。 オブジェクトに属する任意のプロパティをアニメーション化できます。非視覚プロパティでも同様です。  
  
 次の図は、「 **MoveUp**」という名前のストーリーボードを示しています。 タイムラインには、四角形の X と Y 位置をマークするキーフレームが含まれています。 このアニメーションを実行すると、四角形はある位置から別の位置にスムーズに移動します。  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 次のビデオを見ると、アニメーションの作成について確認できます。  
  
|短いビデオを見る:|次の方法を確認する:|  
|--------------------------|-------------------|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [タイムラインを作成する](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|タイムラインを作成し、タイムライン内のオブジェクトを使用します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [キーフレームを追加し、アニメーション繰り返す](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|キーフレームを追加し、各キーフレームでプロパティを設定します。 次に、アニメーションを実行し、オブジェクトがスムーズに遷移していることを確認します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [対話機能にイベント トリガーを追加する](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|イベントの発生時にアニメーションを開始します。 たとえば、ウィンドウの読み込み時にアニメーションを開始します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [色をアニメーション化する](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|アニメーションを使用して、オブジェクトの色を変更します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [モーション パスを作成および変更する](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|パスに沿ってオブジェクトをアニメーション化します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [キーフレームを簡略化する](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|アニメーションの動きを、開始近く *(イージング イン)* または終了近く *(イージング アウト)* で加速または減速します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [ボタンをアニメーション化する](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|ユーザーがボタンをマウスでポイントすると表示される面白い効果を作成します。|  
|![インストールされている機能を構成する](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [アニメーションを作成し、イージングを使用する](https://www.youtube.com/watch?v=mAJXYrwxGYo)|ユーザーが電卓のイメージ上のボタンを押した時に表示される効果をアニメーション化します。|  
  
## <a name="see-also"></a>「  
 [Blend for Visual Studio を使用して UI を作成する](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
