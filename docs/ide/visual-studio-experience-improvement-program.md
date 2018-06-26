---
title: カスタマー エクスペリエンス向上プログラム
description: Visual Studio でプライバシー設定を管理する方法を確認します。
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dbc83a2d3fe1b2f5bb32a6baaf336c0a6c46e7d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572635"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio カスタマー エクスペリエンス向上プログラム

Visual Studio カスタマー エクスペリエンス向上プログラム (VSCEIP) は、Microsoft による Visual Studio の改善を時間の経過と共に支援するように設計されています。 このプログラムは、コンピューターでのユーザーのタスクを中断させずにコンピューター ハードウェア、ユーザーの Visual Studio の利用、[エラーに関する情報を収集](../ide/diagnostic-data-collection.md)します。 収集される情報は、Microsoft が改善する機能を特定するために役立ちます。 このドキュメントは、VSCEIP を有効または無効を選択する方法を説明します。

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>オプトインまたはオプトアウト

VSCEIP は既定で有効になっています。 次の手順で、オフにしたり、もう一度でオンにしたりできます。

1. Visual Studio を起動します。

1. **[ヘルプ]** メニューの **[フィードバックの送信]** をポイントして、**[設定]** を選択します。

   **[Visual Studio エクスペリエンス向上プログラム]** ダイアログ ボックスが開きます。

1. オプトアウトするには、**[いいえ、参加しません]** を選んでから、**[OK]** を選びます。
   オプトインするには、**[参加する]** を選んでから、**[OK]** を選びます。

   ![[Visual Studio エクスペリエンス向上プログラム] ダイアログ](media/experience-improvement-program.png)

### <a name="registry-settings"></a>レジストリの設定

[Build Tools for Visual Studio](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017) をインストールする場合は、レジストリを更新して VSCEIP を構成する必要があります。 企業のお客様の場合、レジストリ ベースのポリシーを設定することにより、VSCEIP を有効または無効にするグループ ポリシーを構成できます。

これに関連するレジストリ キーと設定は以下のとおりです。

64 ビット OS の場合: キー = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**  
32 ビット OS の場合: キー = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**  
グループ ポリシーが有効になっている場合: キー = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**  

エントリ = **OptIn**

値 = (DWORD)
- **0**: オプトアウト (VSCEIP をオフにする)
- **1**: オプトイン (VSCEIP をオンにする)

> [!CAUTION]
> レジストリを間違って編集すると、システムが壊れる可能性があります。 レジストリを変更する前に、コンピューターにある重要なデータをバックアップしてください。 手動での変更の適用後に問題が発生した場合は、**[前回正常起動時の構成]** スタートアップ オプションを使うこともできます。

VSCEIP によって収集、処理、または送信される情報については、「[Microsoft のプライバシーに関する声明](https://privacy.microsoft.com/privacystatement)」を参照してください。

## <a name="see-also"></a>関連項目

* [Visual Studio によって収集される診断情報](diagnostic-data-collection.md)
* [ご意見](../ide/talk-to-us.md)
* [Visual Studio 2017 で問題を報告する方法](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)
* [Microsoft のプライバシーに関する声明](https://privacy.microsoft.com/privacystatement)
