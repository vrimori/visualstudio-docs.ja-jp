---
title: '手順 10: その他のボタンおよびチェック ボックスに対するコードの記述'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55c5b2a645c2781f9286b635cd6d1e08dd86137e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882855"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>手順 10: その他のボタンおよびチェック ボックスに対するコードの記述
ここまでで、他の 4 つのメソッドを実行する準備が整いました。 このコードをコピーして貼り付けることもできますが、コードを入力し、IntelliSense を使用すると、このチュートリアルの学習の効果を最大限に高めることができます。

 このコードは、以前に追加したボタンに機能を追加します。 このコードがないと、ボタンは何も実行しません。 コントロールをアクティブにすると、ボタンは <xref:System.Windows.Forms.Control.Click> イベントのコードを使用して (およびチェック ボックスは <xref:System.Windows.Forms.CheckBox.CheckedChanged> イベントを使用して)、異なる内容を実行します。 たとえば、**[Clear the picture]** ボタンをクリックしたときにアクティブになる `clearButton_Click` イベントは **[Image]** プロパティを **null** (または **nothing**) に設定して、現在のイメージを消去します。 コードの各イベントには、コードが実行する内容を説明するコメントが含まれています。

 ![ビデオへのリンク](../data-tools/media/playvideo.gif)このトピックのビデオ版については、「[Tutorial 1:Create a picture viewer in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216)」(チュートリアル 1: Visual Basic によるピクチャ ビューアーの作成 - ビデオ 5) または「[Tutorial 1:Create a picture viewer in C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206)」(C# によるピクチャ ビューアーの作成 - ビデオ 5) をご覧ください。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。

> [!NOTE]
>  ベスト プラクティスとして、コードには常にコメントを付けることをお勧めします。 コメントは人が読むための情報であり、時間をかけてでも記述しておけばコードがわかりやすくなります。 コメント行の内容は、プログラムではすべて無視されます。 行をコメント行にするには、Visual C# の場合は先頭に 2 つのスラッシュ (//) を入力し、Visual Basic の場合は先頭に単一引用符 (') を入力します。

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>その他のボタンとチェック ボックスのコードを記述するには

-   次のコードを **Form1** コード ファイル (*Form1.cs* または *Form1.vb*) に追加します。 Visual Basic コードを表示するには **[VB]** タブをクリックします。

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>続行または確認するには

-   チュートリアルの次の手順に進むには、「[手順 11:プログラムの実行とその他の機能の使用](../ide/step-11-run-your-program-and-try-other-features.md)」をご覧ください。

-   チュートリアルの前の手順に戻るには、「[手順 9:レビュー、コメントの追加、およびコードのテスト](../ide/step-9-review-comment-and-test-your-code.md)」をご覧ください。
