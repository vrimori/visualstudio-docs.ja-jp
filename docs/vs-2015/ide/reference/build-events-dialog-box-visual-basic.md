---
title: '[ビルド イベント] ダイアログ ボックス (Visual Basic) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23f1d883468c34d042da3501f4fc88004ebdf44e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539208"
---
# <a name="build-events-dialog-box-visual-basic"></a>[ビルド イベント] ダイアログ ボックス (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ビルド イベント ダイアログ ボックス (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/build-events-dialog-box-visual-basic)します。  
  
  
**[ビルド イベント]** ダイアログ ボックスを使用して、ビルド構成の手順を指定します。 また、ビルド前またはビルド後の任意のイベントを実行する条件を指定することもできます。 詳細については、「[方法 : ビルド イベントを指定する (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)」を参照してください。  
  
 **ビルド前に実行するコマンド ライン**  
 ビルド開始前に実行する任意のコマンドを指定します。 長いコマンドを入力するには、**[ビルド前の編集]** をクリックして [[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)を表示します。  
  
> [!NOTE]
>  プロジェクトが最新の状態で、ビルドがトリガーされない場合、ビルド前イベントは実行されません。  
  
 **ビルド後に実行するコマンド ライン**  
 ビルド終了後に実行する任意のコマンドを指定します。 長いコマンドを入力するには、**[ビルド後の編集]** をクリックして **[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス**を表示します。  
  
> [!NOTE]
>  .bat ファイルを実行するすべてのビルド後コマンドの前に `call` ステートメントを追加します。 たとえば、`call C:\MyFile.bat` または `call C:\MyFile.bat call C:\MyFile2.bat` のようにします。  
  
 **ビルド後イベントの実行**  
 次の表に示すように、実行するビルド後イベントの条件を指定します。  
  
|オプション|結果|  
|------------|------------|  
|**常時**|ビルド後イベントは、ビルドが成功したかどうかに関係なく実行されます。|  
|**ビルドが成功したとき**|ビルド後イベントは、ビルドが成功した場合に実行されます。 このため、ビルドが成功した場合は、最新のプロジェクトについてもイベントが実行されます。 これは、既定の設定です。|  
|**ビルドがプロジェクト出力を更新したとき**|ビルド後イベントは、コンパイラの出力ファイル (.exe または .dll) が以前のコンパイラの出力ファイルと異なる場合にだけ実行されます。 ビルド後イベントは、プロジェクトが最新の場合は実行されません。|  
  
## <a name="see-also"></a>関連項目  
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [方法 : ビルド イベントを指定する (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)



