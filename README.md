import Image from 'next/image';
import Link from 'next/link';
import {
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from "@/components/ui/accordion";

// Emojis for categories
const categoryEmojis: { [key: string]: string } = {
  "Endereço": "📍",
  "Contato": "📱",
  "Horário": "⏰",
  "Site": "💻",
  "Instagram": "📸",
  "Cardápio": "📋",
};

// Data structure for restaurants and units
const restaurants = [
  {
    id: "maria-antonieta",
    name: "Maria Antonieta",
    logo: "/images/maria-antonieta-logo.png",
    logoWidth: 70,
    logoHeight: 18,
    logoClass: "h-4 md:h-5",
    slogan: "Cozinha Italiana Tradicional",
    units: [
      {
        id: "ma-jatiuca",
        name: "Jatiúca",
        details: [
          { label: "Endereço", value: "Av. Dr. Antônio Gomes de Barros, 150 - Jatiúca, Maceió - AL" },
          { label: "Contato", value: "(82) 3202-8828", href: "tel:+558232028828" },
          { label: "Horário", value: "Seg a Sáb 12h às 00h | Dom 12h às 23h" },
          { label: "Site", value: "mariaantonieta-al.com.br", href: "http://www.mariaantonieta-al.com.br/", target: "_blank" },
          { label: "Instagram", value: "@mariaantonieta.maceio", href: "https://www.instagram.com/mariaantonieta.maceio/", target: "_blank" }, // Updated Instagram
          { label: "Cardápio", value: "(Em breve)" } // Placeholder, add PDF link if provided
        ]
      },
      {
        id: "ma-parque",
        name: "Parque Shopping (Em breve)",
        comingSoon: true,
        description: [
          { type: 'heading', text: 'Nova Unidade' },
          { type: 'paragraph', text: 'Estamos animados em anunciar que o Maria Antonieta em breve estará disponível no Parque Shopping Maceió!' },
          { type: 'paragraph', text: 'Fique atento às nossas redes sociais para atualizações sobre a data de inauguração e promoções especiais de abertura.' },
          { type: 'heading', text: 'Detalhes' },
          { type: 'detail', label: "Endereço", value: "Parque Shopping Maceió, Av. Comendador Gustavo Paiva, 5.945 - Cruz das Almas, Maceió - AL" },
          { type: 'detail', label: "Contato", value: "(A confirmar)" },
          { type: 'detail', label: "Horário", value: "(A confirmar)" },
          { type: 'detail', label: "Site", value: "mariaantonieta-al.com.br", href: "http://www.mariaantonieta-al.com.br/", target: "_blank" },
          { type: 'detail', label: "Instagram", value: "@mariaantonieta.maceio", href: "https://www.instagram.com/mariaantonieta.maceio/", target: "_blank" }, // Updated Instagram
          { type: 'heading', text: 'O que esperar' },
          { type: 'paragraph', text: 'Nossa nova unidade no Parque Shopping trará a mesma qualidade e tradição da culinária italiana autêntica que você já conhece e ama do Maria Antonieta Jatiúca.' },
          { type: 'paragraph', text: 'Você poderá desfrutar dos nossos pratos premiados, carta de vinhos selecionada e o atendimento de excelência em um novo ambiente sofisticado e aconchegante.' },
        ]
      }
    ]
  },
  {
    id: "armazem-guimaraes",
    name: "Armazém Guimarães",
    logo: "/images/armazem-guimaraes-logo.png",
    logoWidth: 70,
    logoHeight: 18,
    logoClass: "h-4 md:h-5",
    slogan: "Pizzaria & Trattoria",
    units: [
      {
        id: "ag-jatiuca",
        name: "Jatiúca – Maceió",
        details: [
          { label: "Endereço", value: "Av. Dr. Antônio Gomes de Barros, 188 - Jatiúca, Maceió - AL" },
          { label: "Contato", value: "(82) 3325-4545", href: "tel:+558233254545" },
          { label: "Horário", value: "Seg a Qui: 17h às 23:30 | Sex a Dom: 17h às 00h" },
          { label: "Site", value: "armazemguimaraes.com.br", href: "https://www.armazemguimaraes.com.br/", target: "_blank" },
          { label: "Instagram", value: "@armazemguimaraes", href: "https://www.instagram.com/armazemguimaraes/", target: "_blank" },
          { label: "Cardápio", value: "Ver Cardápio", href: "/menus/armazem-jatiuca-cardapio.pdf", target: "_blank" }
        ]
      },
      {
        id: "ag-parque",
        name: "Parque Shopping - Maceió",
        details: [
          { label: "Endereço", value: "Parque Shopping Maceió, Av. Comendador Gustavo Paiva, 5.945 - Cruz das Almas, Maceió - AL" },
          { label: "Contato", value: "(82) 3025-3440", href: "tel:+558230253440" }, // Updated phone number
          { label: "Horário", value: "Todos os dias – 12h às 22h" },
          { label: "Site", value: "armazemguimaraes.com.br", href: "https://www.armazemguimaraes.com.br/", target: "_blank" },
          { label: "Instagram", value: "@armazemguimaraes", href: "https://www.instagram.com/armazemguimaraes/", target: "_blank" },
          { label: "Cardápio", value: "Ver Cardápio", href: "/menus/armazem-parque-shopping-cardapio.pdf", target: "_blank" }
        ]
      },
      {
        id: "ag-riomar",
        name: "RioMar – Recife",
        details: [
          { label: "Endereço", value: "Shopping RioMar Recife - Av. República do Líbano, 251 - Pina, Recife - PE" },
          { label: "Contato", value: "(81) 99896-0166", href: "tel:+5581998960166" },
          { label: "Horário", value: "Todos os dias - 11h às 22h" },
          { label: "Site", value: "armazemguimaraes.com.br", href: "https://www.armazemguimaraes.com.br/", target: "_blank" },
          { label: "Instagram", value: "@armazemguimaraesrecife", href: "https://www.instagram.com/armazemguimaraesrecife/", target: "_blank" },
          { label: "Cardápio", value: "Ver Cardápio", href: "/menus/armazem-riomar-recife-cardapio.pdf", target: "_blank" }
        ]
      }
    ]
  },
  {
    id: "super-pizza",
    name: "Super Pizza",
    logo: "/images/super-pizza-logo.png",
    logoWidth: 55,
    logoHeight: 36,
    logoClass: "h-7 md:h-8",
    slogan: "Um cheiro irresistível, um sabor inconfundível e um carinho que a gente adora.",
    units: [
      {
        id: "sp-ponta-verde",
        name: "Ponta Verde",
        details: [
          { label: "Endereço", value: "Av. Álvaro Otácilio, 3195 - Ponta Verde, Maceió - AL" },
          { label: "Contato", value: "(82) 3231-1999", href: "tel:+558232311999" },
          { label: "Horário", value: "Todos os dias – 16h às 23h" },
          { label: "Site", value: "superpizza.com.br", href: "https://www.superpizza.com.br/", target: "_blank" },
          { label: "Instagram", value: "@super_pizza", href: "https://www.instagram.com/super_pizza/", target: "_blank" },
          { label: "Cardápio", value: "(Em breve)" } // Placeholder
        ]
      },
      {
        id: "sp-farol",
        name: "Farol",
        details: [
          { label: "Endereço", value: "Av. Fernandes Lima - Farol, Maceió - AL" },
          { label: "Contato", value: "(82) 2122-1950", href: "tel:+558221221950" },
          { label: "Horário", value: "Todos os dias – 16h às 23h" },
          { label: "Site", value: "superpizza.com.br", href: "https://www.superpizza.com.br/", target: "_blank" },
          { label: "Instagram", value: "@super_pizza", href: "https://www.instagram.com/super_pizza/", target: "_blank" },
          { label: "Cardápio", value: "(Em breve)" } // Placeholder
        ]
      },
      {
        id: "sp-maceio-shopping",
        name: "Maceió Shopping",
        details: [
          { label: "Endereço", value: "Maceió Shopping, Av. Comendador Gustavo Paiva, 2990 - Mangabeiras, Maceió - AL" },
          { label: "Contato", value: "(82) 2122-1999", href: "tel:+558221221999" },
          { label: "Horário", value: "10h às 22h" },
          { label: "Site", value: "superpizza.com.br", href: "https://www.superpizza.com.br/", target: "_blank" },
          { label: "Instagram", value: "@super_pizza", href: "https://www.instagram.com/super_pizza/", target: "_blank" },
          { label: "Cardápio", value: "(Em breve)" } // Placeholder
        ]
      },
      {
        id: "sp-parque-shopping",
        name: "Parque Shopping",
        details: [
          { label: "Endereço", value: "Parque Shopping Maceió, Av. Comendador Gustavo Paiva, 5.945 - Cruz das Almas, Maceió - AL" },
          { label: "Contato", value: "(82) 2122-1999", href: "tel:+558221221999" },
          { label: "Horário", value: "10h às 22h" },
          { label: "Site", value: "superpizza.com.br", href: "https://www.superpizza.com.br/", target: "_blank" },
          { label: "Instagram", value: "@super_pizza", href: "https://www.instagram.com/super_pizza/", target: "_blank" },
          { label: "Cardápio", value: "(Em breve)" } // Placeholder
        ]
      },
      {
        id: "sp-shopping-patio",
        name: "Shopping Pátio",
        details: [
          { label: "Endereço", value: "Shopping Pátio Maceió, Av. Menino Marcelo, 3800 - Cidade Universitária, Maceió - AL" },
          { label: "Contato", value: "(82) 2122-1999", href: "tel:+558221221999" },
          { label: "Horário", value: "10h às 22h" },
          { label: "Site", value: "superpizza.com.br", href: "https://www.superpizza.com.br/", target: "_blank" },
          { label: "Instagram", value: "@super_pizza", href: "https://www.instagram.com/super_pizza/", target: "_blank" },
          { label: "Cardápio", value: "(Em breve)" } // Placeholder
        ]
      }
    ]
  }
];

// Component for rendering unit details (now with nested accordion and emojis)
const UnitContent = ({ unit }: { unit: any }) => {
  // Handle the special case for Maria Antonieta Parque Shopping (coming soon)
  if (unit.comingSoon && unit.description) {
    return (
      <div className="space-y-2 text-sm md:text-base"> {/* Increased font size */}
        {unit.description.map((item: any, index: number) => {
          if (item.type === 'heading') {
            return <h4 key={index} className="font-semibold mt-3 mb-1">{item.text}</h4>;
          }
          if (item.type === 'paragraph') {
            return <p key={index} className="mb-1">{item.text}</p>;
          }
          if (item.type === 'detail') {
            const emoji = categoryEmojis[item.label] || '';
            const content = item.href ? (
              <Link href={item.href} target={item.target} className="text-blue-600 hover:underline break-words">
                {item.value}
              </Link>
            ) : (
              <span className="break-words">{item.value}</span>
            );
            return (
              <p key={index} className="mb-1">
                <span className="font-semibold">{emoji}{item.label}:</span> {content}
              </p>
            );
          }
          return null;
        })}
      </div>
    );
  }

  // Standard rendering with nested accordion for details
  return (
    <Accordion type="single" collapsible className="w-full space-y-1">
      {unit.details.map((detail: any, index: number) => {
        const emoji = categoryEmojis[detail.label] || '';
        return (
          <AccordionItem key={index} value={`detail-${index}`} className="border-b last:border-b-0">
            <AccordionTrigger className="hover:no-underline text-sm md:text-base font-medium py-2 px-1 text-left"> {/* Increased font size */}
              {emoji}{detail.label}
            </AccordionTrigger>
            <AccordionContent className="pt-0 pb-2 px-1 text-sm md:text-base"> {/* Increased font size and padding */}
              {detail.href ? (
                <Link href={detail.href} target={detail.target} className="text-blue-600 hover:underline break-words">
                  {detail.value}
                </Link>
              ) : (
                <span className="break-words">{detail.value}</span>
              )}
            </AccordionContent>
          </AccordionItem>
        );
      })}
    </Accordion>
  );
};

export default function Home() {
  return (
    <main className="flex min-h-screen flex-col items-center justify-start pt-12 md:pt-16 px-4 bg-[#F8F6F2]">
      {/* Adjusted max-width for potentially wider content */}
      <div className="z-10 w-full max-w-lg md:max-w-xl items-center justify-center font-sans flex flex-col">
        {/* Main Logo */}
        <div className="mb-4 flex h-20 w-20 md:h-24 md:w-24 items-center justify-center rounded-full bg-[#A02C2C] text-white text-2xl md:text-3xl font-bold">
          GG
        </div>

        {/* Title */}
        <h1 className="mb-1 text-xl md:text-2xl font-bold text-[#A02C2C]">
          GRUPO GUIMARÃES
        </h1>

        {/* Subtitle */}
        <p className="mb-8 text-sm md:text-base text-gray-600">
          Excelência em Gastronomia.
        </p>

        {/* Restaurants Accordion */}
        <div className="w-full">
          <Accordion type="single" collapsible className="w-full space-y-3 md:space-y-4">
            {restaurants.map((restaurant) => (
              <AccordionItem key={restaurant.id} value={restaurant.id} className="bg-white rounded-lg shadow-sm border-none px-4 py-1 md:px-5 md:py-1.5">
                {/* Modified AccordionTrigger for centering */}
                <AccordionTrigger className="hover:no-underline text-gray-800 font-medium text-base md:text-lg py-2">
                  <div className="flex items-center justify-center w-full relative"> {/* Centered content, relative positioning for potential arrow adjustment */}
                    <div className="flex items-center space-x-3 md:space-x-4"> {/* Logo and Name container */}
                      <Image src={restaurant.logo} alt={`${restaurant.name} Logo`} width={restaurant.logoWidth} height={restaurant.logoHeight} className={`object-contain ${restaurant.logoClass}`} />
                      <span>{restaurant.name}</span>
                    </div>
                    {/* The default arrow might be positioned absolutely by the component, or we might need to adjust its position if centering breaks it */}
                  </div>
                </AccordionTrigger>
                <AccordionContent className="pt-2 pb-1 text-gray-700">
                  {/* Nested Accordion for Units */}
                  <Accordion type="single" collapsible className="w-full space-y-2">
                    {restaurant.units.map((unit) => (
                      <AccordionItem key={unit.id} value={unit.id} className="border rounded-md px-3 py-0.5">
                        <AccordionTrigger className="hover:no-underline text-sm md:text-base font-medium py-2"> {/* Increased font size */}
                          {unit.name}
                        </AccordionTrigger>
                        <AccordionContent className="pt-2 pb-1">
                          <UnitContent unit={unit} />
                        </AccordionContent>
                      </AccordionItem>
                    ))}
                  </Accordion>
                </AccordionContent>
              </AccordionItem>
            ))}
          </Accordion>
        </div>

        {/* Footer */}
        <footer className="mt-10 mb-6 text-center text-xs text-gray-500">
          Grupo Guimarães | Todos os direitos reservados.
        </footer>
      </div>
    </main>
  );
}

