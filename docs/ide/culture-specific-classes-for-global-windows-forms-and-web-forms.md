---
title: グローバルな Windows フォームおよび Web フォームにおけるカルチャ固有のクラス
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c311e9c79e4f2861b8b52852ff7bb9b0217bf22c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948038"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>グローバルな Windows フォームおよび Web フォームにおけるカルチャ固有のクラス

各カルチャには、日付、時間、数、通貨などの情報を表示するさまざまな規約があります。 <xref:System.Globalization> 名前空間には、次のようなカルチャ固有の値の表示方法を変更するために使用できるクラスが含まれています。
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>カルチャ設定の使用

アプリまたは **[地域のオプション]** コントロール パネルに保存されているカルチャ設定を使用してカルチャ規約を実行時に判別し、それに応じて情報の形式を設定します。 カルチャの設定の詳細については、「[方法:ASP.NET Web ページのグローバリゼーション用のカルチャおよび UI カルチャを設定する](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)」を参照してください。 カルチャ設定に基づいて情報の形式を自動で設定するクラスは、*カルチャ固有*と呼ばれます。 カルチャ固有のメソッドの例:
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

カルチャ固有の関数 (Visual Basic 言語) には、`MonthName` や `WeekDayName` などがあります。

例として、次のコードに <xref:System.IFormattable.ToString%2A> メソッドを使用して、現在のカルチャで通貨の形式を設定する方法を示します。

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

カルチャが "fr-FR" に設定されている場合は、出力ウィンドウに次が表示されます。

`100,00`

カルチャが "en-US" に設定されている場合は、出力ウィンドウに次が表示されます。

`$100.00`

## <a name="see-also"></a>関連項目

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)