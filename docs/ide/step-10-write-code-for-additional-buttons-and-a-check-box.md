---
title: '手順 10: その他のボタンおよびチェック ボックスに対するコードの記述 | Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13461522bd4e195eec5bc2a681c8c6b1a9def5d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>手順 10: その他のボタンおよびチェック ボックスに対するコードの記述
ここまでで、他の 4 つのメソッドを実行する準備が整いました。 このコードをコピーして貼り付けることもできますが、コードを入力し、IntelliSense を使用すると、このチュートリアルの学習の効果を最大限に高めることができます。  
  
 このコードは、以前に追加したボタンに機能を追加します。 このコードがないと、ボタンは何も実行しません。 コントロールをアクティブにすると、ボタンは `Click` イベントのコードを使用して (およびチェック ボックスは `CheckChanged` イベントを使用して)、異なる内容を実行します。 たとえば、**[Clear the picture]** ボタンをクリックしたときにアクティブになる `clearButton_Click` イベントは `Image` プロパティを `null` (または `nothing`) に設定して、現在のイメージを消去します。 コードの各イベントには、コードが実行する内容を説明するコメントが含まれています。  
  
 ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")このトピックのビデオ版については、「[チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 - ビデオ 5](http://go.microsoft.com/fwlink/?LinkId=205216)」または「[チュートリアル 1: C# によるピクチャ ビューアーの作成 - ビデオ 5](http://go.microsoft.com/fwlink/?LinkId=205206)」を参照してください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。  
  
> [!NOTE]
>  ベスト プラクティスとして、コードには常にコメントを付けることをお勧めします。 コメントは人が読むための情報であり、時間をかけてでも記述しておけばコードがわかりやすくなります。 コメント行の内容は、プログラムではすべて無視されます。 行をコメント行にするには、Visual C# の場合は先頭に 2 つのスラッシュ (//) を入力し、Visual Basic の場合は先頭に単一引用符 (') を入力します。  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>その他のボタンとチェック ボックスのコードを記述するには  
  
-   次のコードを Form1 コード ファイル (Form1.cs または Form1.vb) に追加します。 Visual Basic コードを表示するには **[VB]** タブをクリックします。  
  
     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
-   チュートリアルの次の手順に進むには、「[手順 11: プログラムの実行とその他の機能の使用](../ide/step-11-run-your-program-and-try-other-features.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 9: 確認、コメントの追加、およびコードのテスト](../ide/step-9-review-comment-and-test-your-code.md)」を参照してください。