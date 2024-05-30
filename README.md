# Arbre-App-iOS
App utilisable avec Swift UI sur iOS 



//
//  FunMoV2App.swift
//  CheapFunV2
//
//  Created by apprenant53 on 13/05/2024.
//

import SwiftUI

@main
struct FunMoV2App: App {
    var body: some Scene {
        WindowGroup {
            FinalAppView()
        }
    }
}


---------------------------------------------------------------------------------------------------------------------------------------------------------------------







//
//  ContentView.swift
//  FunMoV2
//
//  Created by apprenant53 on 13/05/2024.
//

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Image(systemName: "globe")
                .imageScale(.large)
                .foregroundStyle(.tint)
            Text("Hello, world!")
        }
        .padding()
    }
}

#Preview {
    ContentView()
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------




//
//  FinalAppView.swift
//  CheapFun
//
//  Created by apprenant53 on 08/05/2024.
//

import SwiftUI

struct FinalAppView: View {
    var body: some View {
        TabView {
            SuggestionsV2()
                .tabItem {
                    Image(systemName: "lightbulb")
                    Text("Suggestion")
                }
            FavorisList()
                .tabItem {
                    Image(systemName: "heart")
                    Text("Favoris")
                }
            ListViewV2()
                .tabItem {
                    Image(systemName: "list.dash.header.rectangle")
                    Text("Liste")
                }
        }
    }
}

#Preview {
    FinalAppView()
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------




//
//  DetailsView.swift
//  FunMoAppTest
//
//  Created by apprenant53 on 03/05/2024.
//

import SwiftUI

struct DetailsView: View {
    
    var data: EventData
    
    @State var isFavorite: EventData
    
    
    @State var isHidden: Bool
    @State var isViewed = false
    
    var body: some View {
        ScrollView {
            VStack {
                Image(data.img)
                    .resizable()
                    .scaledToFit()
                    .frame(width: 360)
                    .cornerRadius(15)
                    .overlay {
                        RoundedRectangle(cornerRadius: 15)
                            .stroke(.mainApp, lineWidth: 10)
                    }
                HStack {
                    Text(data.name)
                        .font(.title)
                    Spacer()
                    Button {
                        isFavorite.isFavorite.toggle()
                    } label: {
                        Image(systemName: isFavorite.isFavorite ? "heart.fill" : "heart")
                            .font(.title)
                            .foregroundStyle(.mainApp)
                    }
                }
                .padding(.top)
                Divider()
                HStack { /*Date*/
                    Text(data.date)
                        .font(.title3)
                        .fontWeight(/*@START_MENU_TOKEN@*/.bold/*@END_MENU_TOKEN@*/)
                    Spacer()
                }
                HStack { /*Place*/
                    Text(data.place)
                        .font(.title3)
                        .foregroundStyle(.gray)
                    Spacer()
                }
                Text(data.description)
                    .font(.footnote)
                    .lineLimit(isViewed ? 10 : 2)
                    .padding(.top, 30)
                
                Button {
                    isViewed.toggle()
                } label: {
                    Image("plusButton")
                        .foregroundStyle(.mainApp)
                }
                .padding(.top, 2)
                .overlay {
                    Image(systemName: isViewed ? "minus" : "plus")
                        .foregroundStyle(.white)
                        .font(.footnote)
                        .padding(.top, 2)
                        .fontWeight(.bold)
                }
                .drawingGroup()
                .padding(.top)
                HStack {
                    Text(data.price)
                        .font(.title)
                        .foregroundStyle(.mainApp)
                        .fontWeight(/*@START_MENU_TOKEN@*/.bold/*@END_MENU_TOKEN@*/)
                    Spacer()
                    Button {
                        //                    Action
                    } label: {
                        Label("Réserver", systemImage: "ticket.fill")
                            .foregroundStyle(.white)
                            .padding()
                            .fontWeight(.bold)
                            .background {
                                RoundedRectangle(cornerRadius: 12.0)
                                    .foregroundStyle(.mainApp)
                            }
                    }
                }
                .padding(.top, 20)
            }
            .padding(.top, 50)
            .padding(.horizontal)
        }
    }
}

#Preview {
    DetailsView(data: EventData(name: "Projection", img: "jsg-yap-J39X2xX_8CQ-unsplash", type: "Cinema", date: "14.06", price: "10€", place: "Videodrome - Cours Julien", description: "", hour: ""), isFavorite: EventData(name: "", img: "", type: "", date: "", price: "", place: "", description: "", hour: ""), isHidden: true)
}

------------------------------------------------------------------------------------------------------------------------------------------------------------------




//
//  EventBlock.swift
//  CheapFun
//
//  Created by apprenant53 on 07/05/2024.
//

import SwiftUI

struct EventBlock: View {
    

    
    var data = EventData(name: "", img: "freaks", type: "", date: "", price: "", place: "", description: "", hour: "")
    
    
    
    var body: some View {
        VStack (alignment: .leading)  {
            ZStack (alignment: .topLeading){
                Image(data.img)
                    .resizable()
                    .scaledToFill()
                    .frame(maxWidth: 180, maxHeight: 120)
                    .cornerRadius(7)
                    .overlay {
                        RoundedRectangle(cornerRadius: 7)
                            .stroke(lineWidth: 4)
                            .foregroundStyle(Color.mainApp)
                    }
//                HStack {
//                    Image(systemName: "heart")
//                        .font(.title2)
//                        .foregroundStyle(.white)
//                        .bold()
//                        .padding()
//                }
            }
            VStack (alignment: .leading) {
                Text(data.name)
                    .fontWeight(.semibold)
                    .foregroundStyle(.black)
                Text(data.type)
                    .font(.footnote)
                    .foregroundStyle(.black)
                HStack {
                    Text(data.price)
                        .font(.headline)
                        .fontWeight(.heavy)
                        .foregroundStyle(Color.mainApp)
                    Spacer()
                    Text(data.date)
                        .font(.subheadline)
                        .fontWeight(.regular)
                        .foregroundStyle(Color.mainApp)
                    Image(systemName: "calendar")
                        .font(.title2)
                        .foregroundStyle(Color.mainApp)
                    
                }
            }
        }
    }
}

#Preview {
    EventBlock(data: EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "14.06", price: "11€", place: "Couvent - Belle de Mai", description: "", hour: ""))
}


------------------------------------------------------------------------------------------------------------------------------------------------------------------



//
//  FavEventBlock.swift
//  FunMoV2
//
//  Created by apprenant53 on 14/05/2024.
//

import SwiftUI

struct FavEventBlock: View {
    
    var data = EventData(name: "", img: "freaks", type: "", date: "", price: "", place: "", description: "", hour: "")
    
    
    var body: some View {
        VStack (alignment: .leading)  {
            ZStack (alignment: .topLeading){
                Image(data.img)
                    .resizable()
                    .scaledToFill()
                    .frame(maxWidth: 180, maxHeight: 120)
                    .cornerRadius(7)
                    .overlay {
                        RoundedRectangle(cornerRadius: 7)
                            .stroke(lineWidth: 4)
                            .foregroundStyle(Color.mainApp)
                    }
                HStack {
                    Image(systemName: "heart.fill")
                        .font(.title2)
                        .foregroundStyle(.mainApp)
                        .bold()
                        .padding()
                }
            }
            VStack (alignment: .leading) {
                Text(data.name)
                    .fontWeight(.semibold)
                    .foregroundStyle(.black)
                Text(data.type)
                    .font(.footnote)
                    .foregroundStyle(.black)
                HStack {
                    Text(data.price)
                        .font(.headline)
                        .fontWeight(.heavy)
                        .foregroundStyle(Color.mainApp)
                    Spacer()
                    Text(data.date)
                        .font(.subheadline)
                        .fontWeight(.regular)
                        .foregroundStyle(Color.mainApp)
                    Image(systemName: "calendar")
                        .font(.title2)
                        .foregroundStyle(Color.mainApp)
                    
                }
            }
        }
    }
}

#Preview {
    FavEventBlock()
}

------------------------------------------------------------------------------------------------------------------------------------------------------------------



//
//  TagView.swift
//  FunMo
//
//  Created by apprenant53 on 07/05/2024.
//

import SwiftUI

struct TagView: View {
    @Binding var selectedTag: Set<String>
    
    var tags = ["Cinema", "Sports", "Expos", "Musique", "Nature", "Art", "Ateliers"]
    
    var body: some View {
        ScrollView(.horizontal, showsIndicators: false) {
            HStack {
                ForEach(tags, id: \.self) { tag in
                    Text(tag)
                        .padding()
                        .background(selectedTag.contains(tag) ? .mainApp: .gray)
                        .clipShape(RoundedRectangle(cornerRadius: 15, style: .continuous))
                        .onTapGesture {
                            if selectedTag.contains(tag) {
                                selectedTag.remove(tag)
                            } else {
                                selectedTag.insert(tag)
                            }
                        }
                }
            } .foregroundStyle(.white)
        }
    }
}

struct TagViewContainer: View {
    
    @State var selectedTag: Set<String> = []
    
    var body: some View {
        TagView(selectedTag: $selectedTag)
    }
}

#Preview {
    TagViewContainer()
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------



//
//  EventBlockList.swift
//  FunMo
//
//  Created by apprenant53 on 08/05/2024.
//

import SwiftUI

struct EventBlockList: View {
    var data = EventData(name: "", img: "freaks", type: "", date: "", price: "", place: "", description: "", hour: "")
    
    var body: some View {
        VStack {
            ZStack (alignment: .topLeading){
                Image(data.img)
                    .resizable()
                    .scaledToFill()
                    .frame(maxWidth: 400, maxHeight: 200)
                    .cornerRadius(7)
                    .overlay {
                        RoundedRectangle(cornerRadius: 7)
                            .stroke(lineWidth: 8)
                            .foregroundStyle(Color.mainApp)
                    }
                HStack {
                    Image(systemName: "heart")
                        .font(.title2)
                        .foregroundStyle(.white)
                        .bold()
                        .padding()
                }
            }
            VStack (alignment: .leading) {
                Text(data.name)
                    .font(.title2)
                    .fontWeight(.semibold)
                    .foregroundStyle(.black)
                Text(data.type)
                    .font(.title3)
                    .foregroundStyle(.black)
                HStack {
                    Text(data.price)
                        .font(.title3)
                        .fontWeight(.heavy)
                        .foregroundStyle(Color.mainApp)
                    Spacer()
                    Text(data.date)
                        .font(.title3)
                        .fontWeight(.regular)
                        .foregroundStyle(Color.mainApp)
                    Image(systemName: "calendar")
                        .font(.title2)
                        .foregroundStyle(Color.mainApp)

                    
                }
            }
        }
    }
}

#Preview {
    EventBlockList(data: EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "14.06", price: "11€", place: "Couvent - Belle de Mai", description: "", hour: ""))
}




------------------------------------------------------------------------------------------------------------------------------------------------------------------
//
//  EventBlockList.swift
//  FunMo
//
//  Created by apprenant53 on 08/05/2024.
//

import SwiftUI

struct EventBlockList: View {
    var data = EventData(name: "", img: "freaks", type: "", date: "", price: "", place: "", description: "", hour: "")
    
    var body: some View {
        VStack {
            ZStack (alignment: .topLeading){
                Image(data.img)
                    .resizable()
                    .scaledToFill()
                    .frame(maxWidth: 400, maxHeight: 200)
                    .cornerRadius(7)
                    .overlay {
                        RoundedRectangle(cornerRadius: 7)
                            .stroke(lineWidth: 8)
                            .foregroundStyle(Color.mainApp)
                    }
                HStack {
                    Image(systemName: "heart")
                        .font(.title2)
                        .foregroundStyle(.white)
                        .bold()
                        .padding()
                }
            }
            VStack (alignment: .leading) {
                Text(data.name)
                    .font(.title2)
                    .fontWeight(.semibold)
                    .foregroundStyle(.black)
                Text(data.type)
                    .font(.title3)
                    .foregroundStyle(.black)
                HStack {
                    Text(data.price)
                        .font(.title3)
                        .fontWeight(.heavy)
                        .foregroundStyle(Color.mainApp)
                    Spacer()
                    Text(data.date)
                        .font(.title3)
                        .fontWeight(.regular)
                        .foregroundStyle(Color.mainApp)
                    Image(systemName: "calendar")
                        .font(.title2)
                        .foregroundStyle(Color.mainApp)

                    
                }
            }
        }
    }
}

#Preview {
    EventBlockList(data: EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "14.06", price: "11€", place: "Couvent - Belle de Mai", description: "", hour: ""))
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------




//
//  FavorisList.swift
//  FunMo
//
//  Created by apprenant53 on 08/05/2024.
//

import SwiftUI

struct FavorisList: View {
    
    
    var eventV = [
        EventData(name: "Projection : Burning", img: "Capture d’écran 2024-04-19 à 20.45.42", type: "Cinéma", date: "14.06", price: "Prix Libre", place: "Couvent - Belle de Mai", description: "Lors d’une livraison, Jongsu, un jeune coursier, retrouve par hasard son ancienne voisine, Haemi, qui le séduit immédiatement. De retour d’un voyage à l’étranger, celle-ci revient cependant avec Ben, un garçon fortuné et mystérieux.", hour: ""),
        EventData(name: "Color Bus", img: "Colorbus-Marseille-Sightseeing-Tour-893x534", type: "Tourisme", date: "24.06", price: "5€", place: "", description: "Tour des principaux points touristiques de la ville comme Notre Dame de la Garde, le Mucem, la cathédrale de la Major...", hour: ""),
        EventData(name: "Concert Plein Air", img: "yvette-de-wit-NYrVisodQ2M-unsplash", type: "Musique", date: "28.06", price: "12€", place: "Parc Borély", description: "Plongez dans une atmosphère envoûtante lors de notre événement de concerts en plein air. Sous le ciel étoilé, laissez-vous emporter par une soirée magique où la musique rencontre la nature. Des artistes locaux se produiront sur scène, offrant un mélange éclectique de genres musicaux, des mélodies enivrantes du jazz aux rythmes enflammés du rock.", hour: ""),
        EventData(name: "Avant-Première", img: "jeremy-yap-J39X2xX_8CQ-unsplash", type: "Cinéma", date: "14.06", price: "7€", place: "Cinéma Les Variétés", description: "Sélections de films d'auteurs en avant-première", hour: ""),
        EventData(name: "Atelier Sushis", img: "vinicius-benedit--1GEAA8q3wk-unsplash", type: "Atelier", date: "14.06", price: "11€", place: "Restaurant le Yen", description: "Découverte de ce célèbre art culinaire Japonais avec un chef Sushis spécialement venu pour l'occasion. Vous découvrirez en groupe les différentes étapes de préparation de cet incontournable de la culture nippone", hour: ""),
        EventData(name: "Initiation Bch.Volley", img: "jannes-glas-0NaQQsLWLkA-unsplash", type: "Sport", date: "30.06", price: "5€", place: "Plage du Prado", description: "Découvrez le Beach volley, un sport dynamique et ensoleillé qui combine compétition et plaisir sous le soleil éclatant des plages. Joué sur du sable fin, ce sport exige rapidité, agilité et communication entre coéquipiers. Avec ses règles simples et son ambiance décontractée, le Beach volley est parfait pour se divertir entre amis ou en famille.", hour: ""),
        EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "14.06", price: "10€", place: "Videodrome", description: "La Monstrueuse Parade, souvent désigné sous son titre anglais original Freaks, est un film américain réalisé par Tod Browning, sorti en 1932. Le film a également été exploité sous d’autres titres : Barnum en France , Forbidden Love, The Monster Show ou Nature's Mistakes en anglais.", hour: "20h30")
    ]
    
    
    var body: some View {
        NavigationStack {
            VStack {
                HStack {
                    Text("Trier")
                        .fontWeight(.bold)
                    Image(systemName: "arrow.up.arrow.down")
                        .foregroundStyle(.mainApp)
                    Spacer()
                }
                .padding(.top, 40)
                .padding(.horizontal, 10)
                Divider()
                    .padding(.bottom)
                    .padding(.horizontal, 10)
                ScrollView {
                    LazyVGrid(columns: [GridItem(.flexible()), GridItem(.flexible())]) {
                        ForEach(eventV) { events in
                            NavigationLink {
                                DetailsView(data: events, isFavorite: EventData(name: "", img: "", type: "", date: "", price: "", place: "", description: "", hour: ""), isHidden: true)
                            } label: {
                                FavEventBlock(data: events)
                            }
                        }
                    }
                    .padding(.horizontal, 10)
                    .padding(.top, 2)
                }
            }
        }
    }
}


#Preview {
    FavorisList()
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------




//
//  ListViewV2.swift
//  FunMo
//
//  Created by apprenant53 on 08/05/2024.
//

import SwiftUI

struct ListViewV2: View {
    var eventV = [
        EventData(name: "Projection : Burning", img: "Capture d’écran 2024-04-19 à 20.45.42", type: "Cinéma", date: "14.06", price: "Prix Libre", place: "Couvent - Belle de Mai", description: "Lors d’une livraison, Jongsu, un jeune coursier, retrouve par hasard son ancienne voisine, Haemi, qui le séduit immédiatement. De retour d’un voyage à l’étranger, celle-ci revient cependant avec Ben, un garçon fortuné et mystérieux.", hour: ""),
        EventData(name: "Color Bus", img: "Colorbus-Marseille-Sightseeing-Tour-893x534", type: "Tourisme", date: "24.06", price: "5€", place: "", description: "Tour des principaux points touristiques de la ville comme Notre Dame de la Garde, le Mucem, la cathédrale de la Major...", hour: ""),
        EventData(name: "Concert Plein Air", img: "yvette-de-wit-NYrVisodQ2M-unsplash", type: "Musique", date: "28.06", price: "12€", place: "Parc Borély", description: "Plongez dans une atmosphère envoûtante lors de notre événement de concerts en plein air. Sous le ciel étoilé, laissez-vous emporter par une soirée magique où la musique rencontre la nature. Des artistes locaux se produiront sur scène, offrant un mélange éclectique de genres musicaux, des mélodies enivrantes du jazz aux rythmes enflammés du rock.", hour: ""),
        EventData(name: "Avant-Première", img: "jeremy-yap-J39X2xX_8CQ-unsplash", type: "Cinéma", date: "14.06", price: "7€", place: "Cinéma Les Variétés", description: "Sélections de films d'auteurs en avant-première", hour: ""),
        EventData(name: "Atelier Sushis", img: "vinicius-benedit--1GEAA8q3wk-unsplash", type: "Atelier", date: "14.06", price: "11€", place: "Restaurant le Yen", description: "Découverte de ce célèbre art culinaire Japonais avec un chef Sushis spécialement venu pour l'occasion. Vous découvrirez en groupe les différentes étapes de préparation de cet incontournable de la culture nippone", hour: ""),
        EventData(name: "Initiation Bch.Volley", img: "jannes-glas-0NaQQsLWLkA-unsplash", type: "Sport", date: "30.06", price: "5€", place: "Plage du Prado", description: "Découvrez le Beach volley, un sport dynamique et ensoleillé qui combine compétition et plaisir sous le soleil éclatant des plages. Joué sur du sable fin, ce sport exige rapidité, agilité et communication entre coéquipiers. Avec ses règles simples et son ambiance décontractée, le Beach volley est parfait pour se divertir entre amis ou en famille.", hour: ""),
    ]
    
    
    
    var body: some View {
        NavigationStack {
            VStack {
                HStack {
                    Text("Trier")
                        .fontWeight(.bold)
                    Image(systemName: "arrow.up.arrow.down")
                        .foregroundStyle(.mainApp)
                    Spacer()
                }
                .padding(.top, 40)
                .padding(.horizontal, 10)
                Divider()
                    .padding(.bottom)
                    .padding(.horizontal, 10)
                ScrollView {
                    LazyVGrid(columns: [GridItem(.flexible())]) {
                        ForEach(eventV) { events in
                            NavigationLink {
                                DetailsView(data: events, isFavorite: EventData(name: "", img: "", type: "", date: "", price: "", place: "", description: "", hour: ""), isHidden: true)
                            } label: {
                                EventBlockList(data: events)
                            }
                        }
                    }
                    .padding(.horizontal, 10)
                    .padding(.top, 5)
                }
            }
        }
    }
}

#Preview {
    ListViewV2()
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------


//
//  PreferenceView.swift
//  FunMo
//
//  Created by apprenant53 on 06/05/2024.
//

import SwiftUI

struct PreferenceView: View {
    
    @Environment(\.dismiss) var dismiss
    
    @State var maxBudgetField: String = ""
    @State var dateField: String = ""
    @State var hourField: String = ""
    @State var localisationField: String = ""
    
    @State var text: String
    
    @State var selectedTag: Set<String> = []

    var body: some View {
        VStack {
            Button {
                dismiss()
            } label: {
                Image("plusButton")
                    .foregroundStyle(.mainApp)
                    .font(.title2)
                    .overlay {
                        Image(systemName: "checkmark")
                            .fontWeight(.bold)
                            .font(.caption2)
                            .foregroundStyle(.white)
                    }
            }
            .padding(.top, 40)
            .padding(.bottom, 30)
            TextField("", text: $maxBudgetField, prompt: Text("Budget Maximum (euros)").foregroundStyle(.white.opacity(0.5)))
                .foregroundStyle(Color.white)
                .padding(10)
                .background(){
                    RoundedRectangle(cornerRadius: 10)
                        .foregroundStyle(Color.mainApp)
                }
                .padding([.top, .bottom])
            TextField("", text: $dateField, prompt: Text("Date : jour/mois").foregroundStyle(.white.opacity(0.5)))
                .foregroundStyle(Color.white)
                .padding(10)
                .background(){
                    RoundedRectangle(cornerRadius: 10)
                        .foregroundStyle(Color.mainApp)
                }
                .padding([.top, .bottom])
            TextField("", text: $hourField, prompt: Text("Heure").foregroundStyle(.white.opacity(0.5)))
                .foregroundStyle(Color.white)
                .padding(10)
                .background(){
                    RoundedRectangle(cornerRadius: 10)
                        .foregroundStyle(Color.mainApp)
                }
                .padding([.top, .bottom])
            TextField("", text: $localisationField, prompt: Text("Lieu").foregroundStyle(.white.opacity(0.5)))
                .foregroundStyle(Color.white)
                .padding(10)
                .background(){
                    RoundedRectangle(cornerRadius: 10)
                        .foregroundStyle(Color.mainApp)
                }
                .padding([.top, .bottom])
        }
        .padding([.horizontal, .top])
        Spacer()
        HStack{
            Spacer()
//            Image(systemName: "arrow.right")
//                .fontWeight(.bold)
//                .foregroundStyle(.mainApp)
        }
        .padding(.horizontal)
        TagView(selectedTag: $selectedTag)
            .padding()
        Spacer()
        
    }
}

#Preview {
    PreferenceView(text: "")
}



//.foregroundStyle(Color.white)
//.padding(10)
//.background(){
//    RoundedRectangle(cornerRadius: 10)
//        .foregroundStyle(Color.mainApp)




//VStack {
//    TextField("Budget Maximum", text: $maxBudgetField)
//    
//    .foregroundStyle(Color.white)
//    .padding(10)
//    .background(){
//        RoundedRectangle(cornerRadius: 10)
//            .foregroundStyle(Color.mainApp)
//    }
//}
//.padding()
//.padding(.top, 50)
//.padding(.bottom, 100)

------------------------------------------------------------------------------------------------------------------------------------------------------------------



//
//  ScrollViewTest.swift
//  FunMo
//
//  Created by apprenant49 on 07/05/2024.
//

import SwiftUI

struct ScrollViewTest: View {
    var event = [
        EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "12.06", price: "Gratuit", place: "Videodrome - Cours Julien", description: "La Monstrueuse Parade, souvent désigné sous son titre anglais original Freaks, est un film américain réalisé par Tod Browning, sorti en 1932. Le film a également été exploité sous d’autres titres : Barnum en France , Forbidden Love, The Monster Show ou Nature's Mistakes en anglais.", hour: "20h30"),
        EventData(name: "Chifoumi", img: "solarium", type: "Expo", date: "17.07", price: "Gratuit", place: "SOMA - Cours Julien", description: "Plongez dans l'univers captivant de l'art contemporain à travers une exposition unique qui transcende les frontières de la créativité. Explorez les œuvres audacieuses et provocantes de talents émergents et établis, offrant un regard profond sur les défis et les beautés de notre époque. De la peinture abstraite à la sculpture immersive, chaque pièce invite à une réflexion profonde sur des thèmes universels tels que l'identité, la nature et la société.", hour: ""),
        EventData(name: "Color Bus", img: "Colorbus-Marseille-Sightseeing-Tour-893x534", type: "Tourisme", date: "24.06", price: "5€", place: "Ville de Marseille", description: "Tour des principaux points touristiques de la ville comme Notre Dame de la Garde, le Mucem, la cathédrale de la Major...", hour: "")
    ]
    var body: some View {
        ScrollView(.horizontal, showsIndicators: false) {
            HStack {
                ForEach(event) { events in
                    NavigationLink {
                        DetailsView(data: events, isFavorite: EventData(name: "", img: "", type: "", date: "", price: "", place: "", description: "", hour: ""), isHidden: true)
                    } label: {
                        ZStack (alignment: .topLeading) {
                            RoundedRectangle(cornerRadius: 10)
                                .foregroundStyle(.mainApp)
                                .frame(maxWidth: 350, maxHeight: 260)
                            VStack {
                                ZStack (alignment: .topLeading){
                                    Image(events.img)
                                        .resizable()
                                        .aspectRatio(contentMode: .fill)
                                        .frame(maxWidth: 340, maxHeight: 190)
                                        .cornerRadius(7)
                                        .padding(5)
                                        .background(Color.mainApp)
                                        .cornerRadius(10)
                                    HStack {
                                        VStack {
                                            Button {

                                            }label: {
                                                Image(systemName: "heart")
                                                    .font(.title2)
                                                    .foregroundStyle(.white)
                                                    .bold()
                                                    .padding()
                                            }
                                        }
                                    }
                                }
                                HStack /*(alignment: .top)*/{
                                    VStack (alignment: .leading){
                                        Text(events.name)
                                            .bold()
                                            .foregroundStyle(.white)
                                            .padding(.trailing)
                                        Text(events.type)
                                            .foregroundStyle(.white)
                                            .padding(.trailing)
                                    }
                                    Text(events.price)
                                        .bold()
                                        .foregroundStyle(.white)
                                        .padding(.trailing)
                                    Image(systemName:"calendar")
                                        .foregroundStyle(.white)
                                    Text(events.date)
                                        .bold()
                                        .foregroundStyle(.white)
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}

#Preview {
    ScrollViewTest()
}



------------------------------------------------------------------------------------------------------------------------------------------------------------------



//
//  SuggestionsV2.swift
//  FunMo
//
//  Created by apprenant53 on 07/05/2024.
//

import SwiftUI

struct SuggestionsV2: View {
    @State var showingModal = false
    
    var eventH = [
        EventData(name: "Projection : Freaks", img: "freaks", type: "Cinéma", date: "14.06", price: "11€", place: "Couvent - Belle de Mai", description: "", hour: ""),
        EventData(name: "Color Bus", img: "Colorbus-Marseille-Sightseeing-Tour-893x534", type: "Tourisme", date: "14.06", price: "11€", place: "Couvent - Belle de Mai", description: "", hour: "")
    ]
    
    var eventV = [
        EventData(name: "Projection : Burning", img: "Capture d’écran 2024-04-19 à 20.45.42", type: "Cinéma", date: "14.06", price: "Prix Libre", place: "Couvent - Belle de Mai", description: "Lors d’une livraison, Jongsu, un jeune coursier, retrouve par hasard son ancienne voisine, Haemi, qui le séduit immédiatement. De retour d’un voyage à l’étranger, celle-ci revient cependant avec Ben, un garçon fortuné et mystérieux.", hour: ""),
        EventData(name: "Color Bus", img: "Colorbus-Marseille-Sightseeing-Tour-893x534", type: "Tourisme", date: "24.06", price: "5€", place: "", description: "Tour des principaux points touristiques de la ville comme Notre Dame de la Garde, le Mucem, la cathédrale de la Major...", hour: ""),
        EventData(name: "Concert Plein Air", img: "yvette-de-wit-NYrVisodQ2M-unsplash", type: "Musique", date: "28.06", price: "12€", place: "Parc Borély", description: "Plongez dans une atmosphère envoûtante lors de notre événement de concerts en plein air. Sous le ciel étoilé, laissez-vous emporter par une soirée magique où la musique rencontre la nature. Des artistes locaux se produiront sur scène, offrant un mélange éclectique de genres musicaux, des mélodies enivrantes du jazz aux rythmes enflammés du rock.", hour: ""),
        EventData(name: "Avant-Première", img: "jeremy-yap-J39X2xX_8CQ-unsplash", type: "Cinéma", date: "14.06", price: "7€", place: "Cinéma Les Variétés", description: "Sélections de films d'auteurs en avant-première", hour: ""),
        EventData(name: "Atelier Sushis", img: "vinicius-benedit--1GEAA8q3wk-unsplash", type: "Atelier", date: "14.06", price: "11€", place: "Restaurant le Yen", description: "Découverte de ce célèbre art culinaire Japonais avec un chef Sushis spécialement venu pour l'occasion. Vous découvrirez en groupe les différentes étapes de préparation de cet incontournable de la culture nippone", hour: ""),
        EventData(name: "Initiation Bch.Volley", img: "jannes-glas-0NaQQsLWLkA-unsplash", type: "Sport", date: "30.06", price: "5€", place: "Plage du Prado", description: "Découvrez le Beach volley, un sport dynamique et ensoleillé qui combine compétition et plaisir sous le soleil éclatant des plages. Joué sur du sable fin, ce sport exige rapidité, agilité et communication entre coéquipiers. Avec ses règles simples et son ambiance décontractée, le Beach volley est parfait pour se divertir entre amis ou en famille.", hour: ""),
    ]
    
    var body: some View {
        NavigationStack {
            VStack {
                HStack {
                    HStack {
                        Image("plusButton")
                            .foregroundStyle(.mainApp)
                        Text("Suggestions")
                            .font(.body)
                            .fontWeight(.bold)
                    }
                    .padding(.horizontal)
                    Spacer()
                    Button {
                        showingModal.toggle()
                    } label: {
                        Image(systemName:"slider.horizontal.3")
                            .fontWeight(.bold)
                            .foregroundStyle(Color("mainAppColor"))
                            .padding()
                    }
                    .sheet(isPresented: $showingModal) {
                        PreferenceView(text: "")
                    }
                }
                ScrollView {
                    HStack {
                        Text("Top 3 de la semaine")
                            .foregroundStyle(.mainApp)
                        Spacer()
                    }
                    .padding(.horizontal)
                    ScrollViewTest()
                        .padding(.horizontal, 7)
                        .shadow(radius: 5)
                    HStack {
                        Text("Toutes les suggestions")
                            .foregroundStyle(.mainApp)
                        Spacer()
                    }
                    .padding(.top, 40)
                    .padding(.horizontal)
                    Divider()
                        .padding(.horizontal)
                        .padding(.bottom)
                    LazyVGrid(columns: [GridItem(.flexible()), GridItem(.flexible())]) {
                        ForEach(eventV) { events in
                            NavigationLink {
                                DetailsView(data: events, isFavorite: EventData(name: "", img: "", type: "", date: "", price: "", place: "", description: "", hour: ""), isHidden: true)
                            } label: {
                                EventBlock(data: events)
                            }
                        }
                    }
                    .padding(.horizontal, 10)
                }
            }
        }
    }
}

#Preview {
    SuggestionsV2()
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------



