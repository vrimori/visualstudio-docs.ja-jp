---
title: "グローバルな Windows フォームおよび Web フォームにおけるカルチャ固有のクラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7eae24ec725509b2a2a6a276ad7f474a079bd952
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>グローバルな Windows フォームおよび Web フォームにおけるカルチャ固有のクラス
各カルチャには、日付、時間、数、通貨などの情報を表示するさまざまな規約があります。 <xref:System.Globalization> 名前空間には、<xref:System.Globalization.DateTimeFormatInfo>、**Calendar**、<xref:System.Globalization.NumberFormatInfo> など、カルチャ固有の値の表示方法を変更するために使用できるクラスが含まれています。  
  
## <a name="using-the-culture-setting"></a>カルチャ設定の使用  
 ただし、ほとんどの場合、アプリケーションまたは **[地域のオプション]** コントロール パネルのどちらかに保存されているカルチャ設定を使用して、規約を実行時に自動で判別しそれに応じて情報の形式を設定できます。 カルチャの設定方法の詳細については、「[方法 : Windows フォームのグローバリゼーション用のカルチャおよび UI カルチャを設定する](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)」または「[方法: ASP.NET Web ページのグローバリゼーション用のカルチャおよび UI カルチャを設定する](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)を参照してください。 カルチャ設定に基づいて情報の形式を自動で設定するクラスは、カルチャ固有と呼ばれます。 カルチャ固有のメソッドには、<xref:System.IFormattable.ToString%2A?displayProperty=fullName>、<xref:System.Console.WriteLine%2A?displayProperty=fullName>、<xref:System.String.Format%2A?displayProperty=fullName> があります。 カルチャ固有の関数 (Visual Basic 言語) には、`MonthName` や `WeekDayName` などがあります。  
  
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
  
 カルチャが "fr-FR" に設定されている場合は、出力ウィンドウの表示は次のようになります。  
  
 `100,00`  
  
 カルチャが "en-US" に設定されている場合は、出力ウィンドウの表示は次のようになります。  
  
 `$100.00`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)
