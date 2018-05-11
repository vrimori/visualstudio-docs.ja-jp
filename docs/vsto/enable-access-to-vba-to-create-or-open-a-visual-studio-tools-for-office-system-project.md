---
title: 作成するか、Visual Studio Tools for the Microsoft Office System プロジェクトを開き VBA へのアクセスを有効にします。
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office System project
ms.custom: ''
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05c7296412ffd3f87433f4790617f4b27ca75ae3
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>作成するか、Visual Studio Tools for the Microsoft Office System プロジェクトを開き VBA へのアクセスを有効にします。

作成したり、Visual Studio Tools for the Microsoft Office System プロジェクトを開く前に明示的に、Microsoft office Applications (VBA) のプロジェクト システムの Visual Basic へのアクセスを有効にする必要があります。

 Microsoft Office の開発プロジェクトに、プロジェクトはアプリケーションの Visual Basic を使用しない場合でもに Applications (VBA) のプロジェクト システムに Microsoft Office Word および Microsoft Office Excel の Visual Basic へのアクセスが必要です。 Visual Basic プロジェクトと C# プロジェクトでは、デザイン時にコントロールをサポートするために Visual Basic for Applications プロジェクト システムを使用します。

 一部の Microsoft Office マクロ ウイルスは、ウイルス感染を広げる手段として Visual Basic for Applications プロジェクト システムを自動化しようとします。 Visual Basic for Applications プロジェクト システムへのアクセスを許可すると、マクロ ウイルスの感染防止に有効な保護手段が削除されます。 ただし、通常のマクロ セキュリティは有効なままであるため、コンピューターでマクロを実行するかどうかは、Office アプリケーションで保持されているマクロ セキュリティ レベルおよび信頼される発行者のリストによって決まります。

> [!NOTE]
> これは開発用のコンピューターにのみ適用されます。 エンドユーザーのコンピューターでは、Office ソリューションの実行を有効になっているは、このオプションは必要ありません。

 Visual Basic for Applications プロジェクト システムへのアクセスを禁止してもウイルスから保護されないことに注意してください。コンピューターがそれ以前に一部のマクロ ウイルスに感染していた場合にも、他の文書へのウイルス感染の防止に役立つだけです。 コンピューターに保護層を追加するこのオプションは、既定では無効になっていますが、セキュリティに関する以下のベスト プラクティスに従えば、このオプションを有効にしてもコンピューターがウイルスに感染しやすくなることはありません。

 Office マクロ ウイルスは高または非常に高いセキュリティ レベルのマクロのみを信頼する Office を実行する検証された既知のソースと、最新のセキュリティ パッチとウイルス検出プログラム情報の最高レベルの保護。

 ウイルスやその他の悪意のあるコードから PC を保護する方法についての詳細については、次を参照してください。 [ http://www.microsoft.com/protect](http://www.microsoft.com/protect)です。

 有効にするにまたは、オプションを無効にすることができます**Visual Basic プロジェクトへのアクセスを信頼**手動でします。

 VBA エラーまたは COM エラーが表示される場合、Office のインストールを修復できます。

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Visual Basic プロジェクトへのアクセスを有効または無効にするには

1. **[ファイル]** タブをクリックします。

2. **[オプション]** をクリックします。

3. をクリックして**トラスト センター**、クリックして**セキュリティ センターの設定**です。

4. **トラスト センター**をクリックして**マクロ設定**です。

5. オンまたはオフに**VBA プロジェクトのオブジェクト モデルへのアクセスを信頼**を有効にするにまたは Visual Basic プロジェクトへのアクセスを無効にします。

6. **[OK]** をクリックします。

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>有効にするにまたは 2007 Microsoft Office system で Visual Basic プロジェクトへのアクセスを無効にするには

1. **ツール**メニュー Word または Excel では、をポイント**マクロ**、クリックして**セキュリティ**です。

2. **セキュリティ**ダイアログ ボックスで、をクリックして、**信頼できる発行元**タブです。

3. を有効にするかオフにすると、無効にするには、を選択**Visual Basic プロジェクトへのアクセスを信頼**です。

4. **[OK]** をクリックします。

## <a name="to-set-your-office-macro-security-level"></a>Office マクロのセキュリティ レベルを設定するには

1. **[ファイル]** タブをクリックします。

2. **[オプション]** をクリックします。

3. をクリックして**トラスト センター**、クリックして**セキュリティ センターの設定**です。

4. **トラスト センター**をクリックして**マクロ設定**です。

5. **マクロ設定**セクションで、必要な設定を選択します。

6. **[OK]** をクリックします。

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office system では、Office マクロ セキュリティ レベルを設定するには

1. **ツール**メニュー Word または Excel では、をポイント**マクロ**、クリックして**セキュリティ**です。

2. **セキュリティ レベル** タブで、目的の設定を選択します。

    **セキュリティ レベル** タブには、各レベルの詳細が含まれています。 詳細については、Office ヘルプの「マクロのセキュリティ レベル」を参照してください。

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office システムとともに VBA をインストールするには

1. コントロール パネルで、実行**プログラム追加と削除**または**プログラムと機能**します。

2. Office を選択、**現在インストールされているプログラム** ボックスの一覧です。

3. **[変更]** をクリックします。

4. 選択**削除機能の追加または**、クリックして**続行**です。

5. 選択**アプリケーションのカスタマイズ **、クリックして**次へ**です。

6. 展開**Office 共有機能**で、**アプリケーションおよびツールの更新オプションの選択**  ボックスの一覧です。

7. 横にドロップダウン メニューを開き**アプリケーション用の Visual Basic**、クリックして**マイ コンピューターから実行**です。

8. **[続行]** をクリックします。

9. **[閉じる]** をクリックします。

## <a name="to-repair-your-installation-of-office"></a>Office のインストールを修復するには

1. コントロール パネルで、実行**プログラム追加と削除**または**プログラムと機能**します。

2. Office のバージョンを選択して、**現在インストールされているプログラム** ボックスの一覧です。

3. **[変更]** をクリックします。

4. 選択**を再インストールまたは修復**、順にクリック**次**です。

5. 選択**Office のインストールでエラーを検出して修復**、クリックして**インストール**です。

## <a name="see-also"></a>関連項目

 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)