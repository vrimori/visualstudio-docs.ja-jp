---
title: 作成するか、Visual Studio Tools for the Microsoft Office system プロジェクトを開き、VBA へのアクセスを有効にします。
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b1a7be701c9bec45011980ced63051150579ca7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647571"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>作成するか、Visual Studio Tools for the Microsoft Office system プロジェクトを開き、VBA へのアクセスを有効にします。

作成したり、Visual Studio Tools for the Microsoft Office system プロジェクトを開く前に、Microsoft office Applications (VBA) プロジェクト システムの Visual Basic へのアクセスを明示的にする必要があります。

 Microsoft Office 開発プロジェクトでは、プロジェクトがアプリケーションを Visual Basic を使用しない場合でも、Microsoft Office Word および Microsoft Office Excel では、Applications (VBA) プロジェクト システムの Visual Basic へのアクセスが必要です。 Visual Basic プロジェクトと C# プロジェクトでは、デザイン時にコントロールをサポートするために Visual Basic for Applications プロジェクト システムを使用します。

 一部の Microsoft Office マクロ ウイルスは、ウイルス感染を広げる手段として Visual Basic for Applications プロジェクト システムを自動化しようとします。 Visual Basic for Applications プロジェクト システムへのアクセスを許可すると、マクロ ウイルスの感染防止に有効な保護手段が削除されます。 ただし、通常のマクロ セキュリティは有効なままであるため、コンピューターでマクロを実行するかどうかは、Office アプリケーションで保持されているマクロ セキュリティ レベルおよび信頼される発行者のリストによって決まります。

> [!NOTE]
> これは開発用のコンピューターにのみ適用されます。 エンドユーザーのコンピューターでは、Office ソリューションの実行を有効になっている、このオプションは必要ありません。

 Visual Basic for Applications プロジェクト システムへのアクセスを禁止してもウイルスから保護されないことに注意してください。コンピューターがそれ以前に一部のマクロ ウイルスに感染していた場合にも、他の文書へのウイルス感染の防止に役立つだけです。 コンピューターに保護層を追加するこのオプションは、既定では無効になっていますが、セキュリティに関する以下のベスト プラクティスに従えば、このオプションを有効にしてもコンピューターがウイルスに感染しやすくなることはありません。

 最新のセキュリティ パッチとウイルス スキャナーと Office マクロ ウイルスが高、非常に高いセキュリティ レベルのマクロのみを信頼するで Office を実行することを確認、既知のソースからの最高レベルの保護。

 ウイルスやその他の悪意のあるコードから PC を保護する方法の詳細については、次を参照してください。 [ http://www.microsoft.com/protect](http://www.microsoft.com/protect)します。

 有効にするか、オプションを無効にする**Visual Basic プロジェクトへのアクセスを信頼**手動でします。

 VBA エラーまたは COM エラーが表示される場合、Office のインストールを修復できます。

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>有効または Visual Basic プロジェクトへのアクセスを無効にするには

1. **[ファイル]** タブをクリックします。

2. **[オプション]** をクリックします。

3. をクリックして**トラスト センター**、 をクリックし、**セキュリティ センターの設定**します。

4. **トラスト センター**、 をクリックして**マクロ設定**します。

5. オンまたはオフに**VBA プロジェクトのオブジェクト モデルへのアクセスを信頼**有効または Visual Basic プロジェクトへのアクセスを無効にします。

6. **[OK]** をクリックします。

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>有効または 2007 Microsoft Office system を使用した Visual Basic プロジェクトへのアクセスを無効にするには

1. **ツール**メニューをポイントする Word または Excel で**マクロ**、順にクリックします**セキュリティ**します。

2. **セキュリティ**ダイアログ ボックスで、をクリックして、**信頼された発行元**タブ。

3. 選択して有効にする、またはオフにすると、無効にするには、 **Visual Basic プロジェクトへのアクセスを信頼**します。

4. **[OK]** をクリックします。

## <a name="to-set-your-office-macro-security-level"></a>Office マクロのセキュリティ レベルを設定するには

1. **[ファイル]** タブをクリックします。

2. **[オプション]** をクリックします。

3. をクリックして**トラスト センター**、 をクリックし、**セキュリティ センターの設定**します。

4. **トラスト センター**、 をクリックして**マクロ設定**します。

5. **マクロ設定**セクションで、目的の設定を選択します。

6. **[OK]** をクリックします。

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office system では、Office マクロ セキュリティ レベルを設定するには

1. **ツール**メニューをポイントする Word または Excel で**マクロ**、順にクリックします**セキュリティ**します。

2. **セキュリティ レベル** タブで、目的の設定を選択します。

    **セキュリティ レベル** タブには、各レベルの詳細が含まれています。 詳細については、Office ヘルプの「マクロのセキュリティ レベル」を参照してください。

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office システムとともに VBA をインストールするには

1. コントロール パネルで、次のように実行します。**プログラム追加と削除**または**プログラムと機能**します。

2. [Office] を選択、**現在インストールされているプログラム**一覧。

3. **[変更]** をクリックします。

4. 選択**の追加と削除機能**、 をクリックし、**続行**。

5. 選択**アプリケーションのカスタマイズ **、クリックして**次へ**です。

6. 展開**Office 共有機能**で、**アプリケーションおよびツールの更新プログラムのオプションを選択**一覧。

7. 横にドロップダウン メニューを開く**アプリケーション用の Visual Basic**、 をクリックし、**マイ コンピューターから実行**します。

8. **[続行]** をクリックします。

9. **[閉じる]** をクリックします。

## <a name="to-repair-your-installation-of-office"></a>Office のインストールを修復するには

1. コントロール パネルで、次のように実行します。**プログラム追加と削除**または**プログラムと機能**します。

2. Office のバージョンを選択、**現在インストールされているプログラム**一覧。

3. **[変更]** をクリックします。

4. 選択**を再インストールまたは修復**、順にクリックします**次**します。

5. 選択**Office のインストールでエラーを検出して修復**、 をクリックし、**インストール**します。

## <a name="see-also"></a>関連項目

 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)